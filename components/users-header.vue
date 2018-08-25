<template>
    <div class="registerHeader">
        <div class="clearfix">
            <a href="/" class="fleft">
                <img src="../assets/img/logo.png" alt="">
            </a>
            <a href="/" class="fright">
                返回福居网首页
                <img src="../assets/img/return.png" alt="">
            </a>
        </div>
    </div>
</template>

<script>
    export default {
        name: "user-header"
    }
</script>

<style scoped>
    .registerHeader{
        width: 100%;
        height: 80px;
        background-color: #fff;
    }
    .registerHeader .clearfix{
        width: 1100px;
        height: 80px;
        margin: 0 auto;
    }
    .registerHeader .clearfix .fleft img{
        width: 120px;
        height: 40px;
        margin-top: 20px;
    }
    .fright{
        float: right;
        height: 80px;
        line-height: 80px;
        color: #666;
        font-size: 14px;
    }
    .registerHeader>div .fright img{
        vertical-align: middle;
    }
</style>