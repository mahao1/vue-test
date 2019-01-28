<template>
  <div>
    <h2 class="header">{{msg}}</h2>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        msg: '我是头部组件'
      }
    }
  }
</script>

<style scoped>
  .header{
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px 0;
  }
</style>
