<template>
  <div class="tips-table">
    <table class="cw-table cw-table--stripes">
      <thead>
        <tr>
          <th>Date</th>
          <th>Author</th>
          <th>Tip</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="tips in dbScan" v-bind:key="tips.date">
          <td>{{getHumanDate(tips.date)}}</td>
          <td>{{tips.author}}</td>
          <td>{{tips.tip}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: "tips-table",
    props: {
      dbScan: {
        type: Array,
        required:true
      }
    },

    methods: {
      getHumanDate(epochDate){
        var date = new Date(epochDate);
        // console.log(date);
        // console.log("getDate: "+date.getDate());
        // console.log("getMonth: "+date.getMonth());
        var humanDate = ((date.getMonth()+1)+"/"+date.getDate()+"/"+date.getFullYear());
        return humanDate;
      }
    }
  }
</script>

<style lang="scss">

  // table {
  //   width: 100%;
  //   border-collapse: collapse;
  // }
  // /* Zebra striping */
  // tr:nth-of-type(odd) {
  //   background: #eee;
  // }
  // th {
  //   background: #333;
  //   color: white;
  //   font-weight: bold;
  // }
  // td, th {
  //   padding: 6px;
  //   border: 1px solid #ccc;
  //   text-align: left;
  // }
</style>
