<template>
  <div>
    <p class="test">
      {{ msg }}<br />
      <button @click="changeMsg">change</button>
    </p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Hello World'
    }
  },
  methods: {
    changeMsg () {
      this.msg = 'Hello Vue'
    }
  }
}
</script>

<style scoped>
.test {
  color: red;
}
</style>