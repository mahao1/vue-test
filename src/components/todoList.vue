<template>
  <div id="todoList">
    <el-row type="flex" class="row-bg" justify="center">
      <el-col :span="24">
        <div class="todolist">
          <div class="todo">
            <h2 class="title">todolist</h2>
            <el-input type="text" v-model="todo" @keyup.enter.native="add"></el-input>
            <el-button type="warning" @click="add">添加</el-button>
          </div>

          <div class="todo-main">
            <div class="processing">
              <h2 class="title">进行任务<span class="red">{{list.length - count}}</span>个</h2>
              <ul class="task-ul">
                <li v-for="(item, index) in list" v-if="!item.checked">
                  <el-checkbox :label="index" v-model="item.checked" @change="saveList">{{item.title}}</el-checkbox>
                  <i class="el-icon-delete" @click="removeItem(index)"></i>
                </li>
              </ul>
            </div>
            <div class="done">
              <h2 class="title">已完成<span class="red">{{count}}</span>个</h2>
              <ul class="task-ul">
                <li v-for="(item, index) in list" v-if="item.checked">
                  <el-checkbox :label="index" v-model="item.checked" @change="saveList">{{item.title}}</el-checkbox>
                  <i class="el-icon-delete" @click="removeItem(index)"></i>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import storage from '../model/storage'
  export default {
    name: "todoList",
    data(){
      return {
        todo: '',
        list: [],//进行中列表
        proArr: [],
        doneArr: [],
        count: 0,
      }
    },
    methods: {
      //添加
      add() {
        this.list.push({
          title: this.todo,
          checked: false
        });
        this.todo = '';
        storage.set('list', this.list);
      },
      //进行任务删除
      removeItem(index) {
        console.log('删除', index);
        this.list.splice(index, 1);
        this.common();
        storage.set('list', this.list);
        storage.set('count', this.count);
      },
      //任务状态改变
      saveList(){
        this.common();
        storage.set('list', this.list);
        storage.set('count', this.count);
      },
      common(){
        let count = 0;
        this.list.forEach(value => {
          if(value.checked == true){
            count++;
          }
        });
        this.count = count;
        console.log(`完成任务数量${this.count},进行任务数量${this.list.length - this.count},`);
      },
    },
    mounted(){
      let list = storage.get('list');
      if(list){//判断list是否存在
        this.list = list;
      }
      let count = storage.get('count');
      if(count){//判断list是否存在
        this.count = count;
      }
    }
  }
</script>

<style scoped>
  .todolist{
    width: 100%;
    margin-bottom: 20px;
  }
  .todo{
    width: 100%;
    background: #51b3a9;
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
  .todo-main{
    background: #bbdbab;
    padding: 10px;
  }
  .processing,
  .done{
    margin-top: 10px;
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
