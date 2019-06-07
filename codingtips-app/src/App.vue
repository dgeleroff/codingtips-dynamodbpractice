<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view/> -->
    <Tips></Tips>
  </div>
</template>

<script>
import Tips from '@/components/Tips.vue'

export default {
  name: 'App',
  components: {
    Tips
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
