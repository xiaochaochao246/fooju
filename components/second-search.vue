<template>
    <div class="secondList-content">
        <div class="content-top">
            <a href="/">福居网</a> >
            <a href="/">二手房</a>
        </div>
        <div class="content-search clearfix">
            <input type="text" placeholder="搜索" class="text fleft">
            <input type="button" value="搜索" class="btn fleft">
        </div>
    </div>
</template>

<script>
    export default {
        name: "second-search"
    }
</script>

<style scoped>
    .secondList-content{
        width: 1100px;
        margin:20px auto 0;
    }
    .secondList-content>.content-top{
        font-size: 14px;
        margin-top: 20px;
    }
    .secondList-content>.content-top a{
        color: #999;
    }
    .secondList-content .content-search{
        margin-top: 40px;
    }
    .secondList-content .content-search .text{
        width: 740px;
        height: 60px;
        background-color: #f4f4f4;
        border:none;
        padding-left: 20px;
        border-bottom-left-radius: 3px;
        border-top-left-radius: 3px;
        font-size: 14px;
        outline: none;
        color: #999;
    }
    .secondList-content .content-search .btn{
        border-top-right-radius: 3px;
        border-bottom-right-radius: 3px;
        border: none;
        width: 160px;
        height: 60px;
        color:#fff;
        line-height: 60px;
        text-align: center;
        background-color: #c30d23;
    }
</style>