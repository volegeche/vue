<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <LibraryTable/> -->
    <!-- <SlotParent/> -->
    <slot-2-parent></slot-2-parent>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import LibraryTable from './components/LibraryTable.vue'
// import SlotParent from './components/slot/SlotParent.vue'
import Slot2Parent from './components/slot2/Slot2Parent.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    // LibraryTable,
    // SlotParent,
    Slot2Parent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
