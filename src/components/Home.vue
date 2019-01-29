<template>
  <div id="home">
    <v-header :title="title" :run="run" :home="this" ref="header"></v-header>
    <br>
    <p>{{msg}}</p>
    <div>父组件给子组件传值步骤：</div>
    <div>1、父组件调用子组件的时候，绑定动态属性</div>
    <div>2、在子组件里面通过props接收父组件传递过来的数据</div>
    <div>3、直接在子组件里使用</div>

    <button @click="getChildMethod()">父组件主动获取子组件的数据和方法</button>
  </div>
</template>

<script>
  /*
  * 父组件给子组件传值步骤：
  *
  * 1、父组件调用子组件的时候，绑定动态属性
  * 2、在子组件里面通过props接收父组件传递过来的数据
  * 3、直接在子组件里使用
  *
  * 父组件主动获取子组件的数据和方法：
  *   1、调用子组件的时候定义一个ref
  *     <v-header ref="header"></v-header>
  *   2、在父组件里面使用
  *     this.$refs.header.属性 / this.$refs.header.方法
  */
  import Header from '@/components/Header.vue'
  export default {
    name: "",
    data(){
      return {
        msg: '我是home组件',
        title: '我是首页11'
      }
    },
    methods:{
      run(data){
        alert('我是父组件的方法: '+data);
      },
      getChildMethod(){
        this.$refs.header.child();
      }
    },
    components: {
      'v-header': Header,
    }
  }
</script>

<style scoped>

</style>
