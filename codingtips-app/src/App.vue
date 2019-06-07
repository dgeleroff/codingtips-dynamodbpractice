<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view/> -->
    <Tips></Tips>
    <add-tip></add-tip>
  </div>
</template>

<script>
import Tips from '@/components/Tips.vue'
import AddTip from '@/components/AddTip.vue'

export default {
  name: 'App',
  components: {
    Tips,
    AddTip
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
