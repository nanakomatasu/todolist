<template>
    <div>
    <!-- 头部部分 -->
    <header class="header">
      <h1>todos</h1>
      <input class="new-todo" placeholder="请输入任务名称" autofocus v-model="msg"
        @keydown.enter="addfn">
    </header>
    </div>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
          msg:''
        };
    },
    computed: {

    },
    created() {

    },
    mounted() {

    },
    watch: {

    },
    methods: {
      addfn(){
        if (!this.msg.trim()) return alert('task 名称为空 请先输入')
        this.$emit('add',{
          name:this.msg,  
          id:Date.now(),
          isDone:false
        })
        this.msg = ''
      }
    },
    components: {

    },
};
</script>

<style scoped lang="scss">

</style>
