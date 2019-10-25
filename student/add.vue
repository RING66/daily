<template>
    <!--<el-divider></el-divider>-->

    <el-form :model="form" :rules="rules" ref="form" label-width="80px">
    <el-form-item label="姓名" prop="username">
        <el-input v-model="form.username">
            <i slot="prefix" class="el-input-icon el-icon-user"></i>>
        </el-input>
    </el-form-item>
    <el-form-item label="性别" prop="sex">
        <el-radio-group v-model="form.sex" placeholder="Sex">
            <el-radio label="男"></el-radio>
            <el-radio label="女"></el-radio>
        </el-radio-group>
    </el-form-item>
    <el-form-item label="年龄" prop="age">
        <el-input v-model="form.age">
            <i slot="prefix" class="el-input-icon el-icon-user"></i>>
        </el-input>
    </el-form-item>
    <el-form-item label="班级" prop="classes">
        <el-select v-model="form.classes" placeholder="请选择">
            <el-option
                    v-for="item in  classes"
                    :key="item.cid"
                    :label="item.label"
                    :value="item.cname">
            </el-option>
        </el-select>
    </el-form-item>
    <el-form-item label="联系方式" prop="tell">
        <el-input v-model="form.tell" placeholder="Tell">
            <i slot="prefix" class="el-input-icon el-icon-user"></i>
        </el-input>
    </el-form-item>
    <el-form-item label="学号" prop="num">
        <el-input v-model="form.num" placeholder="Num">
            <i slot="prefix" class="el-input-icon el-icon-user"></i>
        </el-input>
    </el-form-item>

    <el-form-item label="密码 " prop="password">
        <el-input v-model="form.password" placeholder="password">
            <i slot="prefix" class="el-input-icon el-icon-user"></i>
        </el-input>
    </el-form-item>
    <el-form-item>
        <el-button type="primary" @click="submitForm('form') ">提交</el-button>
        <el-button @click="resetForm('form')">重置</el-button>
    </el-form-item>

</el-form>
</template>

<script>
    export default {
        name: "add",
        data: function () {
            return {
                form: {
                    id: '',
                    username: '',
                    sex: '',
                    age: '',
                    classes: '',
                    num: '',
                    tell: '',
                    password: ''

                },
                classes: [{cid: 1, cname: 'wuif1907-2'}, {cid: 2, cname: 'wuif1907-3'}, {cid: 3, cname: 'wuif1907-4'}],
                rules: {
                    username: [
                        { required: true, message: '请输入姓名', trigger: 'blur' },
                        { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                    ],
                    password: [
                        { required: true, message: '请输入密码', trigger: 'blur' }
                    ],
                    sex: [
                        { required: true, message: '请选择性别', trigger: 'blur' }
                    ],
                    age: [
                        { required: true, message: '请输入年龄', trigger: 'blur' }
                    ],
                    classes: [
                        { required: true, message: '请选择班级', trigger: 'blur' }
                    ],
                    num: [
                        { required: true, message: '请输入学号', trigger: 'blur' }
                    ],
                    tell: [
                        { required: true, message: '请输入电话号码', trigger: 'blur' }
                    ]
                }


            }

        },




        methods:{
            submitForm(form) {
                // 改变this指向 箭头函数（定义时就绑定了this的指向） ，this赋给一个临时de变量，函数定义时bind绑定this
                this.$refs[form].validate((valid) => {
                    if (valid) {
                        this.form.id=Date.now();
                      alert(this.form.id);
                        localStorage.form=JSON.stringify(this.form);

                    }else{
                            return false;
                        }
                })
            },
            resetForm(form) {
                this.$refs[form].resetFields();
            }


        }
    }
</script>

<style scoped>

</style>