<template>
    <!--<el-breadcrumb>-->
    <!--<el-breadcrumb-item></el-breadcrumb-item>-->
    <!--<el-breadcrumb-item></el-breadcrumb-item>-->
        <!--&gt;-->
    <!--</el-breadcrumb>-->
    <div class="form" v-if="form">
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
    </div>
</template>

<script>
    export default {
        name: "edit",
        data: function () {
            return {
                form: null,
                classes: [{cid: 1, cname: 'wuif1907-2'}, {cid: 2, cname: 'wuif1907-3'}, {cid: 3, cname: 'wuif1907-4'}],
                id:0
            }
            },
        methods:{
            submitForm(){

            },
            getStudent(){
               let from= localStorage.getItem('form')
                if(from){
                    this.form=JSON.parse(from);
                }else{
                    this.$message.warning('表单不存在');
                }
            }
        },
        beforeMount() {
            this.id=this.$route.params.id;
            this.getStudent();
        }

    }
</script>

<style scoped>

</style>