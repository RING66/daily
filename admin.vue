<template>
    <div>
        <el-container>
            <!--            侧边导航开始-->
            <el-aside width="200px">
                <el-col>
                    <el-menu
                            default-active="2"
                            class="el-menu-vertical-demo">
                        <el-submenu index="1">
                            <template slot="title">
                                <i class="el-icon-setting"></i>
                                <span>学生管理</span>
                            </template>
                            <el-menu-item-group>
                                <el-menu-item index="1-1">
                                    <router-link to="/admin/studentAdd">
                                        添加学生
                                    </router-link>
                                </el-menu-item>
                                <el-menu-item index="1-2">
                                    <router-link to="/admin/studentQuery">
                                        管理学生
                                    </router-link>
                                </el-menu-item>
                            </el-menu-item-group>
                        </el-submenu>
                        <el-submenu index="2">
                            <template slot="title">
                                <i class="el-icon-menu"></i>
                                <span>教师管理</span>
                            </template>
                            <el-menu-item-group>
                                <el-menu-item index="2-1">添加教师</el-menu-item>
                                <el-menu-item index="2-2">管理教师</el-menu-item>
                                <el-menu-item index="2-3">选项1</el-menu-item>
                                <el-menu-item index="2-4">选项2</el-menu-item>
                            </el-menu-item-group>
                        </el-submenu>

                        <el-submenu index="3">
                            <template slot="title">
                                <i class="el-icon-setting"></i>
                                <span>日报可视化</span>
                            </template>
                            <el-menu-item-group>
                                <el-menu-item index="1-1">
                                    <router-link to="/admin/vcharts">
                                        数据可视化
                                    </router-link>
                                </el-menu-item>

                            </el-menu-item-group>
                        </el-submenu>

                        <el-submenu index="4">
                            <template slot="title">
                                <i class="el-icon-message"></i>
                                <span>导航一</span>
                            </template>
                            <el-menu-item-group>
                                <el-menu-item index="4-1">选项1</el-menu-item>
                                <el-menu-item index="4-2">选项2</el-menu-item>
                                <el-menu-item index="4-3">选项1</el-menu-item>
                                <el-menu-item index="4-4">选项2</el-menu-item>
                            </el-menu-item-group>
                        </el-submenu>
                    </el-menu>
                </el-col>
            </el-aside>

            <!--            侧边导航结束-->

            <!--            头部开始-->
            <el-container>
                <el-header style="padding: 0">
                    <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" >
                        <el-menu-item index="1">处理中心</el-menu-item>
                        <el-menu-item index="2">处理中心</el-menu-item>
                        <el-menu-item index="3">处理中心</el-menu-item>

                        <el-submenu index="4">
                            <template slot="title">我的工作台</template>
                            <el-menu-item index="2-1">选项1</el-menu-item>
                            <el-menu-item index="2-2">选项2</el-menu-item>
                            <el-menu-item index="2-3">选项3</el-menu-item>
                            <el-submenu index="2-4">
                                <template slot="title">选项4</template>
                                <el-menu-item index="2-4-1">选项1</el-menu-item>
                                <el-menu-item index="2-4-2">选项2</el-menu-item>
                                <el-menu-item index="2-4-3">选项3</el-menu-item>
                            </el-submenu>
                        </el-submenu>
                    </el-menu>
                </el-header>
                <el-main>
                    <router-view>

                    </router-view>
                </el-main>
                <el-footer>Footer</el-footer>
            </el-container>
        </el-container>
    </div>
</template>

<script>
    export default {
        name: "admin",
        data() {
            return {
               user:null,
            }
        },
        methods: {
            getUser(){
                this.user=JSON.parse(localStorage.getItem('user'))
            },
            handleSelect(key, keyPath) {
                window.console.log(key, keyPath);
            },
            getItem(){

            }
        }
    }
</script>
<style>
    *{
        margin: 0;
        padding: 0;
    }
</style>
<style scoped>
    .el-header, .el-footer {
        background-color: #B3C0D1;
        color: #333;
        text-align: center;
        line-height: 60px;
    }

    /*.el-footer{*/
    /*    position: absolute;*/
    /*    left: 0px;*/
    /*    right:0 ;*/
    /*    top:0px;*/
    /*    bottom: 60px;*/
    /*}*/
    .el-aside {
        background-color: #D3DCE6;
        color: #333;
        text-align: center;
        line-height: 200px;
    }
    .el-menu{
        background-color: #D3DCE6;
    }
    .el-menu-item-group{
        background-color: #D3DCE6;
    }

    .el-main {
        background-color: #E9EEF3;
        color: #333;
        text-align: center;
        line-height: 160px;
    }

    body > .el-container {
        margin-bottom: 40px;
    }

    .el-container:nth-child(5) .el-aside,
    .el-container:nth-child(6) .el-aside {
        line-height: 260px;
    }

    .el-container:nth-child(7) .el-aside {
        line-height: 320px;
    }
    a{
        color: #333333;
    }
    .router-link-exact-active{
        color: rgba(59, 120, 185, 0.59);
    }
</style>