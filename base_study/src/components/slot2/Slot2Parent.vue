<!--
作用域插槽
这个命名来自于学习时的博客，并没有深究该叫法的官方性。
与默认插槽或者具名插槽没什么不同。

个人理解 插槽：就是留空（也就是钩子的一种）
好比公交站（地铁站里）的广告栏，它规定了区域，让使用模板（该有插槽的组件）的时候，去实现对应的模块。

默认插槽：是预先设计，若没人重写覆盖该插槽区域就显示默认，比如广告栏的 “广告位出租”

具名插槽：有时候一个插槽并不能满足需求，因为我们发现即使是广告位，也不可以任意设计，他必须包含几个模块信息，广告商啊，地址啊，版权信息啊等等，
那这样插槽只用默认就无法指定 位置提供给广告商（父组件，或者说使用插槽模板者）设计了。为了解决这问题就出现了具名插槽，去指定部位。

作用域插槽：这个感觉就是具名插槽的一种实现，又感觉不能这么说。这个课题意义奇怪。
感觉唯一存在的意义就是 父组件如何获取插槽内的属性 父组件如何传递值给子组件。
这个操作感觉破坏了 一个组件的完整性。
-->
<template>
  <div>
      <!-- :data将数据信息传递给my-table -->
    <my-table :data="tableData">
        <!-- v-slot="slotPr" 获取该插槽的（所有标签内属性？我猜）属性信息对象 并指定该对象为 slotPr（自定义属性名称）下面代码获取了person（自定义）属性 -->
      <template v-slot="slotPr">
        <span
          :style="{
            color: slotPr.person.tag === '家' ? '#409eff' : '#67c23a',
            backgroundColor:
              slotPr.person.tag === '家' ? '#ecf5ff' : '#f0f9eb'
          }"
          >{{ slotPr.person.tag }}</span
        >
      </template>
    </my-table>
  </div>
</template>

<script>
import MyTable from './Table.vue'
export default {
  components: {
    MyTable
  },
  data () {
    return {
      tableData: [
        {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区',
          tag: '家'
        },
        {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区',
          tag: '公司'
        },
        {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区',
          tag: '家'
        },
        {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区',
          tag: '公司'
        }
      ]
    }
  }
}
</script>