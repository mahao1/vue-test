<template>
  <div id="brotherB">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>{{msg}}</span>
        <el-button style="float: right; padding: 3px 0" type="text" @click="getAData">接收组件A的数据</el-button>
      </div>
      <div>
        <span>此处是接收组件A的数据: </span><el-tag v-show="flag" type="success">{{title}}</el-tag>
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
        msg: '我是组件B',
        title: '',
        flag: false
      }
    },
    mounted(){
      // 用$on事件来接收参数
      Bus.$on('title', (data) => {
        console.log(data);
        this.title = data;
      })
    },
    methods: {
      getAData(){
        this.flag = true;
      }
    }
  }
</script>

<style scoped>

</style>
