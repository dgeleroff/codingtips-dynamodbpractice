<template>
  <div class="tips-table">
    <table>
      <tr>
        <th>Date</th>
        <th>Author</th>
        <th>Tip</th>
      </tr>
      <tr v-for="tips in dbScan" v-bind:key="tips.date">
        <td>{{getHumanDate(tips.date)}}</td>
        <!-- <td>{{tips.date}}</td> -->
        <td>{{tips.author}}</td>
        <td>{{tips.tip}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
  export default {
    name: "tips-table",
    // data () {
    //   return {
    //       dbScan: []
    //   }
    // },
    props: {
      dbScan: {
        type: Array,
        required:true
      }
    },

    methods: {
      getHumanDate(epochDate){
        var date = new Date(0);
        var strDate = epochDate.toString();
        if(strDate.length > 10){
          // console.log("about to trim " + strDate);
          strDate.slice(0,11);
          // console.log("trimmed " + strDate);
          epochDate = parseInt(strDate, 10);
        }
        // console.log(epochDate);
        date.setUTCSeconds(epochDate)
        var humanDate = (date.getDate()+"/"+date.getDay()+"/"+date.getFullYear());
        return humanDate;
      }
    }
  }
</script>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  /* Zebra striping */
  tr:nth-of-type(odd) {
    background: #eee;
  }
  th {
    background: #333;
    color: white;
    font-weight: bold;
  }
  td, th {
    padding: 6px;
    border: 1px solid #ccc;
    text-align: left;
  }
</style>
