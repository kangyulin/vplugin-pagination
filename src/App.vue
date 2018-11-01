<template>
  <div id="app">
    <pagination 
      :total="form.total"
      :page-index="form.pageIndex"
      :page-size="form.pageSize"
      :page-index-change="pageIndexChange" 
      :page-size-change="pageSizeChange"></pagination>
    <div>index:{{form.pageIndex}}</div>
    <div>size:{{form.pageSize}}</div>
  </div>
</template>

<script>
import Pagination from './plugin/pagination'
export default {
  name: 'app',
  data () {
    return {
      form:{
        total: 1000,
        pageIndex: 2,
        pageSize: 20,
      }
    }
  },
  methods:{
    pageIndexChange:function(index){
      this.form.pageIndex = index
      console.log("pageIndexChange:",index,this.form);
    },
    pageSizeChange:function(size){
      this.form.pageSize = size
      console.log("pageSizeChange",size,this.form);
    }
  },
  components:{
    Pagination
  }
}
</script>
