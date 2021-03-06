
:::demo 可以根据单个字段进行排序
```html
<template>
    <div>
        <v-table
             :width="1100"
             :multiple-sort="tables.multipleSort"
             :columns="tables.columns"
             :table-data="tables.tableData"
             @sort-change="sortChange"
             row-hover-color="#eee"
             row-click-color="#edf7ff"
        ></v-table>
    </div>
</template>

<script>

    import mockData from '../../mock/tableData.js'

    export default{
        name: 'sort-by-single-columns',
        data(){
            return {
                tables: {
                    tableData: [],
                    multipleSort:false,
                    columns: [
                        {field: 'name', title: '姓名', width: 100, titleAlign: 'center',columnAlign:'center',orderBy:'asc'},
                        {field: 'tel', title: '手机号码', width: 260, titleAlign: 'center',columnAlign:'center',orderBy:'asc'},
                        {field: 'hobby', title: '爱好', width: 380, titleAlign: 'center',columnAlign:'center'},
                        {field: 'address', title: '地址', titleAlign: 'center',columnAlign:'left'}
                    ]
                }
            }
        },
        methods: {
            getTableData(){
                var vm = this

                setTimeout(function () {
                    vm.tables.tableData = mockData
                }, 10)
            },

            // 获取 table 组件每次操作后的参数（重新去请求数据）
            sortChange(params){
                console.log(params)
            }
        },
        created(){
            this.getTableData()
        }
    }
</script>
```
:::
