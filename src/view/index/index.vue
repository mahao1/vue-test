<template>
  <div id="index" class="layout">

    <todoList></todoList>
    <Home></Home>

  </div>
</template>

<script>
  import todoList from '@/components/todoList'

  import Home from '../../components/Home'
  export default {
    name: "index",
    data(){
      return {

      }
    },
    components: {
      todoList,
      Home
    }
  }
</script>

<style scoped>
  @import 'index.css';
</style>
