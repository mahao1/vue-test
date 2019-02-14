<template>
  <div id="parent">
    <div class="left">
      <div class="title">父子组件传值：</div>
      <el-card class="box-card">
        <div slot="header" class="clearfix">
          <span>{{msg}}</span>
          <el-button style="float: right; padding: 3px 0" type="text" @click="getChildData()">父组件主动获取子组件的数据和方法</el-button>
        </div>
        <div class="sub-title">父组件给子组件传值步骤：</div>
        <ul class="ul">
          <li>1、父组件调用子组件的时候，绑定动态属性: <el-tag type="success">:title="title" :run="run" :home="this"</el-tag></li>
          <li>2、在子组件里面通过props接收父组件传递过来的数据: <el-tag type="success">props: ['title', 'run', 'home']</el-tag></li>
          <li>3、直接在子组件里使用: <el-tag type="success">{{title}}</el-tag></li>
        </ul>
        <div class="sub-title">父组件主动获取子组件的数据和方法：</div>
        <ul class="ul">
          <li>1、调用子组件的时候定义一个ref: ref="child"</li>
          <li>2、在父组件里面使用: this.$refs.child.属性 / this.$refs.child.方法</li>
        </ul>
      </el-card>
    </div>
    <div class="right">
      <!--子组件Child-->
      <Child :title="title" :run="run" :home="this" ref="child"></Child>
    </div>

  </div>
</template>

<script>
  /*
  * 父组件给子组件传值步骤：
  * 1、父组件调用子组件的时候，绑定动态属性
  *   :title="title" :run="run" :home="this"
  * 2、在子组件里面通过props接收父组件传递过来的数据
  *   props: ['title', 'run', 'home'],
  * 3、直接在子组件里使用
  *   {{title}}
  *
  * 父组件主动获取子组件的数据和方法：
  *   1、调用子组件的时候定义一个ref
  *     <Child ref="child"></Child>
  *   2、在父组件里面使用
  *     this.$refs.child.属性 / this.$refs.child.方法
  *
  * 子组件主动获取父组件的数据和方法：
  *   this.$parent.属性 / this.$parent.方法
  *
  */
  import Child from '@/components/Child.vue'

  export default {
    name: "",
    components: {
      Child
    },
    data(){
      return {
        msg: '我是父组件',
        title: '我是父组件的title'
      }
    },
    methods:{
      run(data){
        alert('我是父组件的run方法: '+data);
      },
      getChildData(){
        /*父组件主动获取子组件的数据和方法*/
        this.$refs.child.child();
      }
    },
  }
</script>

<style scoped>
  .ul{
    margin-bottom: 20px;
  }
  .el-tag{
    margin: 5px;
  }
</style>
