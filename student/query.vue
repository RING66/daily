<template>
    <el-table
            :data="students"
            style="width: 150%">
        <el-table-column
                prop="id"
                label="ID"
                width="50">
        </el-table-column>
        <el-table-column
                prop="username"
                label="姓名"
                width="150">
        </el-table-column>
        <el-table-column
                prop="password"
                label="密码"
                width="150">
        </el-table-column>
        <el-table-column
                prop="age"
                label="年龄"
                width="50">
        </el-table-column>

        <el-table-column
                prop="sex"
                label="性别"
                width="50">
        </el-table-column>
        <el-table-column
                prop="num"
                label="学号"
                width="150">
        </el-table-column>
        <el-table-column
                prop="tell"
                label="联系方式"
                width="150">
        </el-table-column>
        <el-table-column
                prop="classes"
                label="班级"
                width="150">
        </el-table-column>


        <el-table-column label="操作">
            <template slot-scope="scope">

                <router-link :to="{ name:'studentEdit',params:{id:scope.row.id}}" tag="el-button"> 编辑
                </router-link>
                <el-button
                        size="mini"
                        type="danger"
                        @click="handleDelete(scope.row.id)">删除
                </el-button>
            </template>
        </el-table-column>
    </el-table>

</template>

<script>
    import student from '../../data/student';

    export default {

        name: "query",
        data() {
            return {
                students: []
            }
        },
        methods: {
            //获取所有数据，
            getStudent() {
                let form = JSON.parse(localStorage.getItem('form'));

                student.push(form);
                window.console.log(this.students);
                this.students = student;
                window.console.log(this.student)
            },
            handleDelete(id) {
                //    findIndex splice
                this.students = this.students.filter(ele => ele.id != id)
            }
        },
        mounted() {
            this.getStudent();
        }
    }
</script>

<style scoped>

</style>