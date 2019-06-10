<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view/> -->
    <tips-table v-bind:dbScan='dbScan'></tips-table>
    <br/>
    <add-tip v-on:add:tip="addTipToTable"></add-tip>
  </div>
</template>

<script>
import axios from 'axios'

import TipsTable from '@/components/TipsTable.vue'
import AddTip from '@/components/AddTip.vue'

export default {
  name: 'App',
  components: {
    TipsTable,
    AddTip
  },
  data() {
    return {
      dbScan: []
    }
  },
  created: function() {
      const client = axios.create({
        baseURL: 'https://laux4mb483.execute-api.us-east-1.amazonaws.com/default/tips'
      })

      client.get('/')
        .then((response) => {
          // console.log(response.data)
          this.dbScan = response.data.Items
        })
        .catch((error) => {
          console.log(error)
        })
  },
  methods: {
    addTipToTable(tip){
        console.log("Hey from Apps.vue!\n Tip is: ");
        console.log(tip);
        tip.date = new Date().getTime();
        this.dbScan.push(tip);
    }
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
