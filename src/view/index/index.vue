<template>
  <div id="index">
    <todoList></todoList>
  </div>
</template>

<script>
  import todoList from '@/components/todoList'
  export default {
    name: "index",
    data(){
      return {

      }
    },
    components: {
      todoList
    }
  }
</script>

<style scoped>
  @import 'index.css';
</style>
