<template>
  <div id="child">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>{{msg}}</span>
        <el-button style="float: right; padding: 3px 0" type="text" @click="run('传的参数123')">执行父组件方法</el-button>
      </div>
      <div class="sub-title">子组件主动获取父组件的数据和方法：</div>
      <ul class="ul">
        <li>this.$parent.属性 或 this.$parent.方法</li>
      </ul>
      <el-button @click="getParent()">获取父组件</el-button>
      <el-button @click="getParentData()">子组件主动获取父组件的数据和方法</el-button>
    </el-card>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        msg: '我是子组件',
      }
    },
    props: ['title', 'run', 'home'],
    methods: {
      getParent(){
        alert(this.home.title);
      },

      child(){
        alert('我是子组件里的child方法');
      },

      getParentData(){
        alert(this.$parent.msg);
        this.$parent.run('哈哈哈');
      }
    }
  }
</script>

<style scoped>
  .ul{
    margin-bottom: 20px;
  }
</style>
