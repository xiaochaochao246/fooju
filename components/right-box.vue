<template>
    <ul class="right-box">
        <li class="box-item">
            <i class="iconfont icon-rili"></i>
            <div class="icon-desc">日程</div>
            <div class="hidden-box">
                我的日程
            </div>
        </li>
        <li class="box-item">
            <i class="iconfont icon-shoucang1"></i>
            <div class="icon-desc">关注</div>
            <div class="hidden-box">
                我的关注
            </div>
        </li>
        <li class="box-item">
            <i class="iconfont icon-fangzi"></i>
            <div class="icon-desc">买房</div>
            <div class="hidden-box">
                在线卖房
            </div>
        </li>
        <li class="box-item">
            <i class="iconfont icon-toolsbar"></i>
            <div class="icon-desc">工具</div>
            <div class="hidden-box">
                房贷计算器
            </div>
        </li>
        <li class="box-item item">
            <i class="iconfont icon-z-phone"></i>
            <div class="icon-desc">APP</div>
            <div class="box-img">
                <img src="../assets/img/app.png" alt="">
            </div>
        </li>
    </ul>
</template>

<script>
    export default {
        name: "right-box"
    }
</script>

<style scoped>
    .right-box{
        position: fixed;
        right:0;
        top:40%;
        transform: translateY(-50%);
        padding:15px 0;
        text-align: center;
        background-color: #fff;
        color:#000;
        z-index:998;
        width: 40px;
    }
    .right-box li .iconfont{
        font-size: 26px;
    }
    .right-box li.item{
        margin-bottom: 0;
    }
    .right-box li{
        position: relative;
        padding:5px 0;
        margin-bottom: 30px;
        cursor: pointer;
    }
    .right-box li:hover{
        color:#fff;
        background-color: #5f1985;
    }
    .right-box li:hover .hidden-box, .right-box li:hover .box-img{
        display: block;
    }
    .hidden-box{
        display: none;
        position: absolute;
        right:50px;
        top:50%;
        transform: translateY(-50%);
        padding:10px;
        background-color: #5f1985;
        color:#fff;
        text-overflow: ellipsis;
        white-space: nowrap;
        border-radius: 4px;
    }
    .hidden-box::after{
        content:"";
        position: absolute;
        right: -16px;
        top:15px;
        transform: translateY(-50%);
        border: 8px solid transparent;
        border-left: 8px solid #5f1985;
    }
    .box-img{
        display: none;
        position: absolute;
        right:35px;
        top:50%;
        transform: translateY(-50%);
        padding:10px;
    }
    .box-img img{
        width: 200px;
        height:200px;
    }
</style>