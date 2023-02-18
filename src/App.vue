<template>
  <section class="todoapp">
    <MyHeader @add="addfn"></MyHeader>
    <MyMain :list="realShowList" @delfn="del"></MyMain>
   <MyFooter :count="count" @setSta="sta" @clearAll="clearAll"/>
    
    
  </section>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import MyFooter from './components/MyFooter.vue';
export default {
 
  data() {
    return {
      list: JSON.parse(localStorage.getItem('todos')) ||[],
      getSta:'all'
    };
  },
  methods:{
    addfn(val){
      this.list.unshift(val)
    },
    del(val){
      this.list=this.list.filter(ele=>ele.id!==val)
    },
    onlog(){
      console.log(this.$refs.footer.msg);
    },
    sta(val){
      this.getSta=val
    },
    clearAll(){
      this.list=this.list.filter(ele=>!ele.isDone)
    }
  },
  computed:{
    count(){
      return this.list.filter(ele=>ele.isDone === false).length
    },
    realShowList(){
      if(this.getSta==='yes'){
        return this.list.filter(ele=>ele.isDone)
      }else if(this.getSta==='no'){
        return this.list.filter(ele=> !ele.isDone)
      }else{
        return this.list
      }
    }
  },
  components:{
    MyFooter:MyFooter,
    MyHeader:MyHeader,
    MyMain:MyMain
  },
  watch:{
    list:{
      handler(val){
        localStorage.setItem('todos',JSON.stringify(val))
      },
      deep:true
    }
  }
}
</script>

<style></style>
