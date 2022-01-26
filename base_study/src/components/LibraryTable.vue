<template>
    <table>
        <tr key="title0" class="test">
            <td colspan="5">图书馆</td>
        </tr>
        <tr key="title1">
            <td colspan="5">图书总量: {{total}}</td>
        </tr>
        <tr key="title2">
            <td>id</td>
            <td>名称</td>
            <td>数量</td>
            <td colspan="3">操作</td>
        </tr>
        <tr v-show="isEdit">
            <td colspan="6"><BookDetail :book="tempBook" @submit="updateSubmit" @cancel="updateCancel"/></td>
        </tr>
        <tr v-for="(book,index) in books" :key="book.id">
            <td>{{book.id}}</td>
            <td>{{book.name}}</td>
            <td>{{book.num}}</td>
            <td><button @click="decrease(index)">减少</button></td>
            <td><button @click="modify(index)">修改</button></td>
            <td><button @click="deleteBook(index)">删除</button></td>
        </tr>
    </table>
</template>

<script lang="ts">
    import BookDetail from './BookDetail.vue'
    import bookEvent from '../js/BookEvent'
    export default{
        components: {
            // HelloWorld
            BookDetail
        },
        data(){
            return {
                books:[
                    {id:'0',name:'西游记',num:5},
                    {id:'1',name:'西游记',num:8},
                    {id:'2',name:'西游记',num:6},
                    {id:'3',name:'西游记',num:2},
                    {id:'4',name:'西游记',num:9}
                ],
                isEdit:false,
                tempBook:{id:null,name:null,num:null}
            }
        },
        computed:{
            total:{
                get:function(){
                    return this.getTotal();
                }
            }
        },
        methods:{
            getTotal:function(){
                var result = 0;
                console.log(this);
                this.books.forEach((book) => {
                    result += book.num; 
                });
                return result;
            },
            decrease:function(index){
                console.log(index);
                this.books[index]['num'] = this.books[index]['num'] - 1;
            },
            deleteBook:function(index){
                console.log("当前下标记："+index);
                this.books.splice(index,1)
            },
            modify:function(index){
                this.tempBook = JSON.parse(JSON.stringify(this.books[index]));
                this.isEdit = true;
            },
            updateSubmit:function(newBook){
                for(var i = 0;i < this.books.length;i++){
                    if(this.books[i].id == newBook.id){
                        // this.books[i].name = newBook.name;
                        // this.books[i].num = Number(newBook.num);
                        this.books[i] = newBook;
                        break;
                    }
                }
                this.tempBook = {id:null,name:null,num:null};
                this.isEdit = false;
            },
            // updateCancel:function(){
            //     this.tempBook = {id:null,name:null,num:null};
            //     this.isEdit = false;
            // }
        },
        watch:{
            books:{
                immediate:true,
                deep:true,
                handler:function(newValue){
                    console.log(newValue);
                }
            }
        },
        mounted () {
            /**
             * 参数1：自定义事件名称
             * 参数2：处理函数
             */
            bookEvent.$on('cancel', () => {
                this.tempBook = {id:null,name:null,num:null};
                this.isEdit = false;
            })
        }
    }

</script>

<style scoped>
    .test{
        color: brown;
        background-color: cadetblue;
    }
</style>