<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view/> -->
    <div class="container">
      <div class="row">
        <div class="col col--md--8">
          <tips-table v-bind:dbScan='dbScan'></tips-table>
        </div>
        <div class="col col--md--4">
          <div class="add-tip card card--shadow-depth-3">
            <add-tip v-on:add:tip="addTipToTable"></add-tip>
          </div>
        </div>
      </div>
      <div class="row">
        <add-tip></add-tip>
      </div>
    </div>
    <br/>
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

<style lang="scss">
@import '~@causeway/core/dist/spa.scss';
@import '~@causeway/core/dist/base/breakpoints';
@import "~@causeway/core/dist/utilities/_variables.scss";
@import "~@causeway/core/dist/utilities/_helpers.scss";
@import "~@causeway/core/dist/base/_icon_backgrounds.scss";
@import "~@causeway/core/dist/base/_breakpoints.scss";
@import "~@causeway/core/dist/base/_buttons.scss";
@import '~@causeway/core/dist/base/display';
@import '~@causeway/core/dist/base/icons';
@import '~@causeway/core/dist/base/lists';
@import "~@causeway/core/dist/base/_tables.scss";
@import "~@causeway/core/dist/base/_forms.scss";
@import "~@causeway/core/dist/base/_grid.scss";
@import "~@causeway/core/dist/blocks/_card.scss";

// #app {
//   font-family: 'Avenir', Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }

.add-tip{
  padding: 10px;
}
</style>
