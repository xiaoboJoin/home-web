<template>
  <div id="example">
    <p>Original message: "{{ message }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <router-link to="/home">About</router-link>
  </div>
</template>

<script>
export default {
  name: 'Example',
  data () {
    return {
      message: 'Welcome to Your Vue.js App'
    }
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
}
</script>
<style>
#example{
  background-color: red
}
</style>


