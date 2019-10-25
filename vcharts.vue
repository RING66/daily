<template>
    <el-row :gutter="10">
        <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1">
            <ve-line :data="chartData"  ></ve-line>
        </el-col>

    </el-row>
</template>

<script>
    export default {
        name: "vcharts",
        data () {
            this.chartSettings = {
                labelMap: {
                    number: '每日提交量',
                }
            }
            return {
                chartData: {
                    columns: ['date', 'number'],
                    rows: [
                        { '日期': '2019-10-24', 'number': 41 },
                        { '日期': '2019-10-24', 'number': 42 },
                        { '日期': '2019-10-24', 'number': 43},
                        { '日期': '2019-10-24', 'number': 44 },

                    ]
                },
                lineData1:{
                    columns:['date','status','skill'],
                    rows:[{date:'7.22',statu:100,skill:0},
                        {date:'8.22',statu:90,skill:20},
                        {date:'9.22',statu:50,skill:50},
                        {date:'10.22',statu:50,skill:50},
                        {date:'11.22',statu:50,skill:50},
                    ]
                }
            }
        }

    }
</script>

<style scoped>

</style>