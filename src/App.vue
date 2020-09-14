<template>
  <div ref="table"></div>
</template>

<script>
var Tabulator = require("tabulator-tables");
// import Tabulator from 'tabulator-tables';

  export default {
    name: 'app',
    data: function () {
      return {
        tabulator: null, //variable to hold your table
        tableData: [], //data for table to display
      }
    },
    watch: {
      //update table if data changes
      tableData: {
        handler: function (newData) {
          this.tabulator.replaceData(newData);
        },
        deep: true,
      }
    },
    mounted() {
      console.log(Tabulator);

      //instantiate Tabulator when element is mounted
      this.tabulator = new Tabulator(this.$refs.table, {
        data: this.tableData, //link data to table
        reactiveData:true, //enable data reactivity
        columns: [], //define table columns
      });
    }
  }
</script>
