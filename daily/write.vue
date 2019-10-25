<template>
    <div>
        <el-divider></el-divider>
        <el-form :model="form" ref="form"  :rules="rules" label-width="80px">
            <el-form-item label="座右铭" prop="motto" >
                <el-input prefix-icon="" v-model="form.motto" placeholder="Motto" clearable
                          minlength="20" maxlength="50" show-word-limit>
                    <i slot="prefix" class="el-input-icon el-icon-user-solid"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="完成情况" prop="finish" >
                <el-input prefix-icon="" v-model="form.finish" placeholder="finish" clearable>
                </el-input>
            </el-form-item>
            <el-form-item label="内容"  prop="content" >
                <el-input type="textarea" minlength="50" prefix-icon="" v-model="form.content" placeholder="content" clearable>
                </el-input>
            </el-form-item>

            <el-form-item label="心得体会" prop="feeling" >
                <el-input prefix-icon="" v-model="form.feeling" placeholder="feeling" clearable>
                </el-input>
            </el-form-item>
            <el-form-item label="遇到问题" prop="problem" >
                <el-input prefix-icon="" v-model="form.problem" placeholder="problem" clearable>
                    <i slot="prefix" class="el-input-icon el-icon-user-solid"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="建议" prop="suggest" >
                <el-input prefix-icon="" v-model="form.suggest" placeholder="suggest" clearable>
                    <i slot="prefix" class="el-input-icon el-icon-user-solid"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="其他" prop="other" >
                <el-input prefix-icon="" v-model="form.other" placeholder="other" clearable>
                    <i slot="prefix" class="el-input-icon el-icon-user-solid"></i>
                </el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('form') ">提交</el-button>
                <el-button @click="resetForm('form')">重置</el-button>
            </el-form-item>

        </el-form>
    </div>
</template>

<script>
    export default {
        name: "write",
        data: function () {
            return {
                form: {
                    names: '',
                    classes: 'wuif1907-2',
                    motto: '',
                    content: '',
                    finish: '',
                    problem:'',
                    feeling:'',
                    suggest:'',
                    other:'',
                },
                classes: [{
                    cid: 1, cname: 'wuif1907-2',
                }, {
                    cid: 2, cname: 'wuif1907-1',
                }, {
                    cid: 3, cname: 'wuif1910',
                }],
                rules: {
                    motto: [
                        {required: true, message: '请输入座右铭', trigger: 'blur'},

                    ],
                    content: [
                        {required: true, message: '请输入内容', trigger: 'blur'},

                    ],
                    problem: [
                        {required: true, message: '请输入你的问题', trigger: 'number'},

                    ],
                    suggest: [
                        {required: true, message: '请输入你的建议', trigger: 'number'},

                    ],

                    finish : [
                        {required: true,  message: '请输入完成度'},

                    ],
                    other: [
                        {required: true, message: '其他', trigger: 'number'},

                    ],
                },
            }

        },
        methods: {
            submitForm() {
                this.form.names=JSON.parse(localStorage.form).username
                fetch('http://www.daily-end.com/index/index/index',{
                       method: 'POST',
                        body: JSON.stringify(this.form),
                        headers:new Headers({
                            'Content-Type': 'application/json'
                        })
                }).then(res=>res.json())
                    .then(data=>{
                    window.console.log(data)
                    if(data.code==200){
                     this.$message.success(data.msg);
                     this.$refs.form.resetFields();
                    }else{
                     this.$message.error(data.msg)
                    }
                })
            }
        }
    }

</script>

<style scoped>
    .el-textarea__inner{

    }
    .form {
        width: 500px;
    }

</style>