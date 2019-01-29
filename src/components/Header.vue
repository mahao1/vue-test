<template>
  <div>
    <h2 class="header">{{msg}} --- {{title}}</h2>
    <button @click="run('传的参数123')">执行父组件方法</button>
    <button @click="getParent()">获取父组件</button>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        msg: '我是头部组件',
        title: '我是子组件'
      }
    },
    props: ['title', 'run', 'home'],
    methods: {
      getParent(){
        alert(this.home.msg);
      },

      child(){
        alert('我是子组件里的方法');
      }
    }
  }
</script>

<style scoped>

</style>
