<template>
  <div id="todoList">
    <el-row type="flex" class="row-bg" justify="center">
      <el-col :span="12">
        <div class="todo">
          <h2 class="title">todolist</h2>
          <el-input type="text" v-model="ipt"></el-input>
          <el-button type="primary" @click="add">添加</el-button>
        </div>

        <div class="processing">
          <h2 class="title">进行任务<span class="red">{{list.length}}</span>个</h2>
          <ul class="task-ul">
            <li v-for="(item, index) in list">
              <el-checkbox :label="index" @change="checkboxChange(item)">{{item}}</el-checkbox>
              <i class="el-icon-delete" @click="removeItem(index)"></i>
            </li>
          </ul>
        </div>
        <div class="done">
          <h2 class="title">已完成<span class="red">{{doneList.length}}</span>个</h2>
          <ul class="task-ul">
            <li v-for="(item, index) in doneList">
              <span>{{item}}</span>
              <i class="el-icon-delete" @click="removeDone(index)"></i>
            </li>
          </ul>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: "todoList",
    data(){
      return {
        ipt: '',
        list: [],//进行中列表
        doneList: [],//完成列表
        checked: false,
        flag: false,
      }
    },
    methods: {
      add(){
        this.list.push(this.ipt);
        this.ipt = '';
      },
      removeItem(index){
        console.log(index);
        this.list.splice(index, 1);
      },
      checkboxChange(val){
        console.log('选择了', val);
        this.flag = true;
        this.list.splice(val, 1);
        this.doneList.push(val);
      },
      removeDone(index){
        console.log('完成', index);
        this.doneList.splice(index, 1);
      }
    }
  }
</script>

<style scoped>
  .todo{
    width: 100%;
    background: #666;
    padding: 10px;
  }
  .title{
    font-size: 20px;
    color: #333;
    margin-bottom: 10px;
  }
  .todo .el-input{
    width: 50%;
  }
  .processing,
  .done{
    margin-top: 10px;
    background: #eee;
    padding: 10px;
  }
  .task-ul{
    width: 50%;
    margin-top: 10px;
    padding: 10px;
  }
  .task-ul li{
    margin-bottom: 10px;
    color: #666;
    background: #fff;
    padding: 10px;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .red{
    color: red;
  }
</style>
