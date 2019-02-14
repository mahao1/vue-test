<template>
  <div id="home">
    <Parent></Parent>
    <div class="brother">
      <div class="title">非父子组件进行传值：</div>
      <el-card class="box-card">
        <div class="sub-title">步骤：</div>
        <ul class="ul">
          <li>1、新建一个bus.js文件，然后引入Vue 实例化Vue并暴露出去: <el-tag>import Vue from 'vue'</el-tag><el-tag>export default new Vue()</el-tag></li>
          <li>2、在要广播的地方引入刚才定义的实例: <el-tag>import Bus from './bus.js'</el-tag></li>
          <li>3、通过<el-tag>Bus.$emit('名称'，'数据')</el-tag>进行广播</li>
          <li>4、在接收数据的地方通过Bus.$on接收广播的数据: <el-tag>Bus.$on('名称', function(data){
            console.log(data);
            })</el-tag></li>
        </ul>
      </el-card>
      <BrotherA></BrotherA>
      <BrotherB></BrotherB>
    </div>
  </div>
</template>

<script>
  import Parent from '@/components/Parent.vue'
  import BrotherA from '@/components/BrotherA.vue'
  import BrotherB from '@/components/BrotherB.vue'
  export default {
    name: "",
    components: {
      Parent,
      BrotherA,
      BrotherB
    },
    data(){
      return {
        msg: '我是home组件',
      }
    },
  }
</script>

<style scoped>
  .brother{
    margin-top: 20px;
  }
  .el-tag{
    margin: 5px;
  }
</style>
