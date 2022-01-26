<template>
    <div>
        <span>id:</span><input type='text' v-model='book.id'/>
        <span>名称:</span><input type='text' v-model='book.name'/>
        <span>数量:</span><input type='text' v-model='book.num'/>
        <button @click="submit">提交</button>
        <button @click="cancel">取消</button>
    </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api'
import bookEvent from '../js/BookEvent'

export default defineComponent({
    props:{
       book:{
           id:String,
           name:String,
           num:Number
       }
    },
    methods:{
        submit:function(){
            /**
             * 参数1：自定义事件的名称
             * 参数2：传递的参数
             */
            this.$emit('submit', this.book);
        },
        cancel:function(){
            bookEvent.$emit('cancel');
        }
    }
})
</script>
