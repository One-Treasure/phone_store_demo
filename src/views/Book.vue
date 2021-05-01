<template>
    <div>
        <table>
            <tr>
                <td>编号</td>
                <td>图书名称</td>
                <td>作者</td>
            </tr>
            <tr v-for="item in books">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.author}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "Book",
        data() {
            return {
                books:[
                    {
                        id: 1,
                        name: 'java基础实战',
                        author: '张三'
                    },
                    {
                        id: 2,
                        name: 'vue基础实战',
                        author: '李四'
                    },
                    {
                        id: 3,
                        name: 'vantUI基础实战',
                        author: '王五'
                    }
                ]
            }
        }
    }
</script>

<style scoped>

</style>