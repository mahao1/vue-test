<template>
  <div id="brotherA">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>{{msg}}</span>
        <el-button style="float: right; padding: 3px 0" type="text" @click="toData">发送组件A的数据</el-button>
      </div>
      <div>
        <span>此处是组件A的数据: </span><el-tag>{{title}}</el-tag>
      </div>
    </el-card>
  </div>
</template>

<script>
  // 引入公共的bus，来做为中间传达的工具
  import Bus from '../api/bus'
  export default {
    name: "",
    data(){
      return {
        msg: '我是组件A',
        title: '我是组件A发送的数据'
      }
    },
    methods: {
      toData(){
        Bus.$emit('title', this.title);
      }
    }
  }
</script>

<style scoped>

</style>
