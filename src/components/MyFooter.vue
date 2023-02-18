<template>
    <div>
    <!-- 底部部分 -->
    <footer class="footer">
      <span class="todo-count"><strong>{{ count }}</strong>剩余</span>
      <ul class="filters">
        <li>
          <a :class="isSta === 'all' ? 'selected' : ''" href="#/" @click="changestatus('all')">全部</a>
        </li>
        <li>
          <a :class="isSta === 'no' ? 'selected' : ''" href="#/active" @click="changestatus('no')">进行中</a>
        </li>
        <li>
          <a :class="isSta === 'yes' ? 'selected' : ''" href="#/completed" @click="changestatus('yes')">已完成</a>
        </li>
      </ul>
      <button class="clear-completed" @click="clear">清除已完成</button>
    </footer>
    </div>
</template>

<script>
export default {
    props: {
      count:Number
    },
    data() {
        return {
        date:'某年',
        isSta:'all'
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
        changestatus(val){
          this.isSta=val
          this.$emit('setSta',this.isSta)
        },
        clear(){
          this.$emit('clearAll')
        }
    },
    components: {

    },
};
</script>

<style scoped lang="scss">

</style>
