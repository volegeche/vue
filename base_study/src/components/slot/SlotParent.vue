<template>
    <div>
        <h1>插槽练习</h1>
        <p>默认插槽练习</p>
        <default-slot></default-slot>
        <default-slot>信息替换！！</default-slot>
        <hr>
        <br>
        <p>具名插槽</p>
        <name-slot>
            <template v-slot:slot1><p>测试信息</p></template>
            <!-- <template #slot2><p>ceshi 信息123456</p></template> -->
        </name-slot>
    </div>
</template>
<script>
import DefaultSlot from './Default.vue';
import NameSlot from './NameSlot.vue';
export default({
    components:{
        NameSlot,
        DefaultSlot
    }
})
</script>

