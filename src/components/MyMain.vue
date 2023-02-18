<template>
    <div>
    <!-- 主体部分 -->
    <section class="main">
      <input id="toggle-all" class="toggle-all" type="checkbox" v-model="issAll"/>
      <label for="toggle-all">Mark all as complete</label>
      <ul class="todo-list">
        <!-- 当任务已完成，可以给 li 加上 completed 类，会让元素加上删除线 -->
        <li :class="item.isDone ? 'completed':''" v-for="item in list" :key="item.id">
          <div class="view">
            <input class="toggle" type="checkbox" v-model="item.isDone" />
            <label>{{item.name}}</label>
            <button class="destroy" @click="del(item.id)" ></button>
          </div>
        </li>
        <!-- <li>
          <div class="view">
            <input class="toggle" type="checkbox" />
            <label>行万里路</label>
            <button class="destroy"></button>
          </div>
        </li> -->
      </ul>
    </section>
    </div>
</template>

<script>
export default {
    props: {
      list:{
        type:Array,
        default:()=>[],
      }
    },
    data() {
        return {
          isAll:true
        };
    },
    computed: {
      issAll:{
        get(){
          return this.list.every(ele=>ele.isDone)
        },
        set(val){
          this.list.forEach(ele=>ele.isDone=val)
        }
      }
    },
    created() {

    },
    mounted() {

    },
    watch: {

    },
    methods: {
      del(id){
        this.$emit('delfn',id)
      }
    },
    components: {

    },
};
</script>

<style scoped lang="scss">

</style>
