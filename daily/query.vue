<!--<template>-->
    <!--<div v-if="dailyArr.length">-->
    <!--<div>学生查看日报</div>-->
        <!--<el-form  :model="form" :inline=""    :rules="rules"  ref="ruleForm"  label-width="80px">-->
            <!--<el-form-item label="内容"  prop="搜索内容">-->
                <!--<el-input v-model="form.content" ></el-input>-->
            <!--</el-form-item>-->
            <!--<el-form-item label="提交时间" prop="">-->
                <!--<el-date-picker-->
                        <!--v-model="form.ctime"-->
                        <!--type="date"-->
                        <!--format="yyyy-MM-dd"-->

                        <!--placeholder="选择日期时间">-->
                <!--</el-date-picker>-->
            <!--</el-form-item>-->
            <!--<el-button-->
                    <!--size="mini"-->
                    <!--type="danger"-->
                    <!--@click="handleDelete(scope.row.id)">删除-->
            <!--</el-button>-->
    <!--<el-table-->
            <!--:data="dailyArr"-->
            <!--style="width: 150%">-->
        <!--<el-table-column-->
                <!--prop="id"-->
                <!--label="ID"-->
                <!--width="50">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="content"-->
                <!--label="姓名"-->
                <!--width="150">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="finish"-->
                <!--label="密码"-->
                <!--width="150">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="suggest"-->
                <!--label="年龄"-->
                <!--width="50">-->
        <!--</el-table-column>-->

        <!--<el-table-column-->
                <!--prop="motto"-->
                <!--label="性别"-->
                <!--width="50">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="feeling"-->
                <!--label="学号"-->
                <!--width="150">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="other"-->
                <!--label="其他"-->
                <!--width="150">-->
        <!--</el-table-column>-->
        <!--<el-table-column-->
                <!--prop="ctime"-->
                <!--label="班级"-->
                <!--width="150">-->
        <!--</el-table-column>-->


        <!--<el-table-column label="操作">-->
            <!--<template slot-scope="scope">-->

                <!--<router-link :to="{ name:'studentEdit',params:{id:scope.row.id}}" tag="el-button"> 编辑-->
                <!--</router-link>-->
                <!--<el-button-->
                        <!--size="mini"-->
                        <!--type="danger"-->
                        <!--@click="getDaily(1)">删除-->
                <!--</el-button>-->
            <!--</template>-->
        <!--</el-table-column>-->
    <!--</el-table>-->

        <!--<el-pagination-->
                <!--page-size="2"-->

                <!--layout="prev, pager, next,jumper"-->
                <!--:total="total">-->
        <!--</el-pagination>-->
    <!--</div>-->
<!--</template>-->

<!--<script>-->
    <!--// import {SUCCESS,FAIL,HOSTNAME} from '../../config/base';-->
    <!--// import MyPage from '../../components/my-page';-->

    <!--export default {-->
        <!--name: "query",-->
        <!--data() {-->
            <!--return {-->
                <!--dailyArr: [],-->
                <!--user:null,-->
                <!--total:0,-->
                <!--limit:2,-->
                <!--form:{-->
                    <!--ctime:'',-->
                    <!--content:''-->
                <!--}-->

            <!--}-->
        <!--},-->
        <!--computed:{-->
          <!--objTQS(){-->
           <!--let str ='';-->
           <!--for(let i in this.form){-->
               <!--let val=this.form[i]-->
               <!--if(val!=''){-->
                   <!--str +='&'+i+'='+val-->
               <!--//对象转换为一个查询字符串 属性连接上一个值-->
               <!--}-->
           <!--}return str;-->
          <!--}-->
        <!--},-->
        <!--methods: {-->
            <!--//获取所有数据，-->
            <!--changePage(){-->
                <!--window.console.log(1)-->
            <!--},-->
            <!--getDaily(i=1) {-->
                <!--let user=this.user.username;-->
                <!--fetch('http://www.daily-end.com/index/index/query?names='+user+'$page='+i+'$limit='+this.limit+objTQS)-->
                    <!--.then(res=>res.json())-->
                    <!--.then(data=>{-->
                        <!--// window.console.log(data);-->
                        <!--if(data.code==200){-->
                            <!--// this.$message.success(data.msg);-->
                            <!--// this.$refs.form.resetFields();-->

                            <!--this.dailyArr=data.data;-->
                            <!--this.total=data.count;-->
                        <!--}else {-->
                            <!--this.$message.error(data.msg)-->
                        <!--}-->
                    <!--})-->
            <!--},-->
            <!--getUser(){-->
                <!--this.user=JSON.parse(localStorage.user)-->
            <!--},-->


            <!--handleDelete(id) {-->
                <!--//    findIndex splice-->
                <!--this.students = this.students.filter(ele => ele.id != id)-->
            <!--}-->
        <!--},-->
        <!--beforeMounte() {-->
            <!--this.getDaily();-->
            <!--this.getUser();-->
        <!--}-->
    <!--}-->
<!--</script>-->

<!--<style scoped>-->

<!--</style>-->