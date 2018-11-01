# 分页控件

### 安装插件
``` bash
npm i vplugin-pagination
```

### 依赖
基于element-ui进行的二次封装,所以外部需要在main.js中引入element-ui
``` vue
import Element from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.use(Element)
```

### 代码示例-main.js
``` vue
import Vue from 'vue'
import App from './App'
import Element from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
import Pagination from 'vplugin-pagination'

Vue.use(Element)
Vue.use(Pagination)
```

### 代码示例-app.vue
``` vue
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
  }
}
</script>
```