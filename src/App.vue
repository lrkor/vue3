<template>
  <customRef msg="Welcome to Your Vue.js App"/>
  <readonly />
</template>

<script>
import customRef from './components/customRef.vue'
import readonly from './components/readonly.vue'

export default {
  name: 'App',
  components: {
    customRef,
    readonly
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
