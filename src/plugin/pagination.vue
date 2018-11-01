<template>
    <el-pagination 
        :pager-count="5"
        :current-page="pageIndex" 
        :page-size="pageSize" 
        :page-sizes="pageSizes" 
        :total="total"
        :layout="layout" 
        @size-change="pageSizeChange" 
        @current-change="pageIndexChange">
    </el-pagination>
</template>

<script>
export default {
    name: "pagination",
    props:{
        total: Number,
        pageIndex: Number,
        pageSize: Number,
        pageSizes: { type: Array, default: function(){ return [10,20,50,100] } },
        pageIndexChange: Function,
        pageSizeChange: Function,
    },
    data(){
        return {
            layout:""
        }
    },
    mounted(){
        this.adaptation()
        window.onresize = () => {
            setTimeout(() => {
                console.log("width:",document.body.clientWidth)
                this.adaptation()
            }, 400);
        }
    },
    methods:{
        adaptation: function(){
            if (document.body.clientWidth > 768)
                this.layout = "total, sizes, prev, pager, next, jumper"
            else
                this.layout = "prev, pager, next"
        }
    }
}
</script>