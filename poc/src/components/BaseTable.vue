<template>
<div>
  <el-radio-group v-model="exportType">
    <el-radio v-for="(item, index) in supportType" :key="index" :label="item" border>{{item}}</el-radio>
  </el-radio-group>
  <el-table
    ref="elTable"
    id="table"
    :data="tableData"
    style="width: 100%">
    <el-table-column
      prop="date"
      label="Date"
      width="180">
    </el-table-column>
    <el-table-column
      prop="name"
      label="Name"
      width="180">
    </el-table-column>
    <el-table-column
      prop="address"
      label="Address">
    </el-table-column>
  </el-table>
  <div style="margin-top: 20px">
    <el-button @click="print">Print</el-button>
    <el-button @click="exportExcel">Export</el-button>
  </div>
</div>
</template>

<script>
import { Printd } from 'printd'
import elTableExport from "el-table-export";

export default {
  name: 'BaseTable',
  data() {
    return {
      supportType: ["csv", "txt", "json", "xls"],
      exportType: "csv",
      tableData: [{
        date: '2016-05-03',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-04',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }]
    }
  },
  methods: {
    print() {
      const styles = [
        'https://unpkg.com/element-ui/lib/theme-chalk/index.css',
      ]
      const scripts = [
        'https://unpkg.com/element-ui/lib/index.js',
      ]
      
      const d = new Printd()
      d.print( document.getElementById('table'), styles, scripts )
      console.log('print')
    },
    exportExcel() {
      elTableExport(this.$refs.elTable, {
        fileName: "export-demo",
        type: this.exportType,
        useFormatter: true,
      })
      .then(() => {
          console.info("ok");
      })
      .catch((err) => {
          console.info(err);
      });
    },
    formatterHandler(row) {
        return "formatter: " + row.remark;
    },
  }
}
</script>