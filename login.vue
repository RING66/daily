<template>
    <div id="box">
    <el-form  :model="ruleForm" :rules="rules"  ref="ruleForm"  label-width="80px">
        <el-form-item label="用户名"  prop="username">
            <el-input v-model="ruleForm.username" ></el-input>
        </el-form-item>
        <el-form-item label="用户密码" prop="password">
            <el-input v-model="ruleForm.password" ></el-input>
        </el-form-item>
        <el-form-item label="用户"  prop="role">
            <!--key关键字-->
            <el-radio v-model="ruleForm.role" v-for="(item,index) in roles" :key="index" :label="item">{{item}} </el-radio>
        </el-form-item>
        <el-form-item>
            <el-button type="primary" @click="submitForm('ruleForm')">确认登录</el-button>
            <el-button @click="resetForm('ruleForm')">取消</el-button>
        </el-form-item>
    </el-form>
    </div>
</template>

<script>
    import admin from '../data/admin';
    import student from '../data/student';
    import teacher from '../data/teacher';
    export default {
        name: "login",
        data: function () {
            return{
                ruleForm:{
                    username:'',
                    password:'',
                    role:[]
            },roles:['teacher','student','admin'],
                rules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur' },
                    { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                ],
                    password: [
                        { required: true, message: '请输入密码', trigger: 'blur' }
                ],
                    role: [
                        { required: true, message: '请选择用户', trigger: 'blur' }
                ]
            }

        }
        },
        methods:{
            submitForm(formName) {
                // 改变this指向 箭头函数（定义时就绑定了this的指向） ，this赋给一个临时de变量，函数定义时bind绑定this
                this.$refs[formName].validate((valid) => {

                    if (valid) {
                        let role=this.ruleForm.role;

                        let model=null;
                       //  alert('submit!');
                       // alert(this);
                        // this.$router.push({path: '/admin'});
                        if(role=='admin'){
                            model=admin;
                            // alert('error submit!!');
                            //  return false;
                        }else if(role=='student'){
                            model=student;
                        }else{
                            model=teacher;
                        }
                        let flag=model.some(ele=>ele.username==this.ruleForm.username&&ele.password==this.ruleForm.password)
                        window.console.log(flag)
                        if(flag){
                            // JSON.stringify(flag[0])
                            localStorage.user=this.form;
                            if(role=='student'){
                                this.$router.push({path:'/student'});
                            }else {
                                this.$router.push({path:'/admin'});
                            }
                            // this.$router.push({path:'/admin'});
                        }else{
                            this.$message.warning('用户名与密码不匹配');
                        }
                    } else{
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.$refs[formName].resetFields();
            }


        }
    }
</script>

<style>
    html,body{
        width:100%;
        height:100%;
        background-image:url("../assets/1.jpg");
        /*background-size:100%;*/
        background-size: cover;
    }
    #box{
        width:300px;
        height:auto;
        position:absolute;
        left:50%;
        top:50%;
        transform: translate(-50%,-50%);
        padding:10px 20px;
        background-color: #dcdcdc42;;
        box-shadow:-3px 6px 16px 0 rgba(0, 0, 0, 0.42);

    }
</style>
<style scoped>
   @import url(https://unpkg.com/element-ui/lib/theme-chalk/index.css);
</style>
