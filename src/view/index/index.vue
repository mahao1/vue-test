<template>
  <div id="index">
    <v-header></v-header>
    <todoList></todoList>

  </div>
</template>

<script>
  import todoList from '@/components/todoList'
  import Header from '@/components/Header.vue'
  export default {
    name: "index",
    data(){
      return {

      }
    },
    components: {
      todoList,
      'v-header': Header
    }
  }
</script>

<style scoped>
  @import 'index.css';
</style>
