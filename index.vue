<template>
  <div id="app">
    <!--<nav class="navbar navbar-default" style="width:500px;margin-left:100px">-->
      <!--<input type="text" v-model="content" class="form-control" placeholder="insert" >-->
      <!--<button type="submit" @click.prevent="insertList" class="btn btn-default">插入</button>-->
    <!--</nav>-->
    <my-input  @zs="insertList"></my-input>
    <my-list  :lists="todolist" seces="success"  @indexdelete="indexdelete"></my-list>

    <!--<div class="panel panel-info">-->
      <!--<ul class="list-group">-->
        <!--<li class="list-group-item" v-for="item in todolist" :key="item.id">-->
          <!--{{item.content}}-->
          <!--<input type="checkbox">-->
          <!--<button @click="deleteList(item.id)">x</button>-->
        <!--</li>-->
      <!--</ul>-->
    <!--</div>-->

  </div>

</template>

<script>
  //引入子组件MyInput
  import MyInput from '../components/my-input';
  import MyList from '../components/my-list';
    export default {
        name: "index",
      components: {
        MyInput,
        MyList
      },
        data:function() {
          return {
            todolist: [
              {id: 1, content: '开题报告，任务书----下周', status: false},
              {id: 2, content: '简历制作----下周四', status: false},
              {id: 3, content: '协同开发上交计划----下周一', status: false},
              {id: 4, content: 'php评审----下周', status: false},
              {id: 5, content: '过程化项目----下周', status: true},
            ],
           // inserdata:{
           //   content:''
           // }
          }

        },
        methods:{
          insertList(value){
            let obj={};
            obj.id=this.todolist[this.todolist.length -1].id+1
            obj.content=value;
            obj.status=false;
            this.todolist.push(obj)
          },
          //删除，找到目标元素的id
         indexdelete(id){
          let index=this.todolist.findIndex(ele=>ele.id==id);
            this.todolist.splice(index,1);
          },
          saveList(){
            this.todolist;
            localStorage.todolist=JSON.stringify(this.todolist);
          },
        },

        watch:{
        //  todolist(){
        //   this.savelist();
        // }
          //深度监听，对todolist进行配置
          todolist:{
            handler:function(){
              this.saveList();
            },
            deep:true
          },
          content(){

          }
        }
    }

</script>

<style scoped>
  .panel{
    width: 300px;
    margin-left:100px;
    border:1px solid darkcyan ;
  }
  ul,li{
    list-style: none;
  }
  .btn-default{
    background: #3a86b9;
  }
  @import url(https://cdn.bootcss.com/twitter-bootstrap/4.3.1/css/bootstrap.css);
</style>