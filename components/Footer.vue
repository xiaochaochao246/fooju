<template>
    <div class="Footer">
        <!--友情链接开始-->
        <div class="fridenship-links">
            <div class="links">
                <div class="title">
                    友情链接
                </div>
                <div class="link-list clearfix">
                    <a href="#" class="fleft" target="_blank">福居网咨询</a>
                    <a href="#" class="fleft" target="_blank">呼和浩特去114</a>
                </div>
            </div>
        </div>
        <!--footer开始-->
        <div class="foot">
            <div class="about">
                <a href="#" target="_blank">关于我们</a>
                <a href="#" target="_blank">联系方式</a>
                <a href="#" target="_blank">隐私声明</a>
                <a href="#" target="_blank">版权声明</a>
                <a href="#" target="_blank">法律保障</a>
            </div>
            <div class="tips">
                温馨提示：呼和浩特房地产网最新购房信息请及时查看呼和浩特房地产业网官方网站【福居网】
            </div>
            <div class="tips">
                地 址：&nbsp;呼和浩特市赛罕区恩和大厦1909室 电 话:400-898-1018
            </div>
            <div class="tips">
                北京福居网网络科技有限公司 Copyright © 2013-2017 FOOJU Corporation, All Rights Reserved 福居网 版权所有|
                <span>京ICP备13012924号-1</span>
            </div>
            <div class="check">
                <a href="#"><img src="../assets/img/21.gif" alt=""></a>
                <a href="#"><img src="../assets/img/pic.gif" alt=""></a>
                <a href="#"><img src="../assets/img/hy.png" alt=""></a>
                <a href="#"><img src="../assets/img/cnnic.png" alt=""></a>
                <a href="#"><img src="../assets/img/cert.png" alt=""></a>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name:"Footer"
    }
</script>
<style scoped>
    /*友情链接*/
    .fridenship-links{
        background-color: #f4f4f4;
        width: 100%;
    }
    .fridenship-links .links{
        width: 1100px;
        margin:0 auto;
        padding:60px 0;
    }
    .fridenship-links .links .title{
        font-size: 30px;
        font-weight: bolder;
        margin-bottom: 30px;
    }
    .fridenship-links .links .link-list a{
        display: inline-block;
        width: 122px;
        font-size: 14px;
        color:#999;
        margin-bottom:10px;
    }
    a,a:hover,a:visited{
        text-decoration: none;
    }
    /*foot开始*/
    .foot{
        width: 100%;
        height: 444px;
        color:#fff;
        background: url(../assets/img/footerBg.png);
    }
    .foot .about{
        width: 100%;
        text-align: center;
        padding-top: 60px;
        margin-bottom: 30px;
    }
    .foot .about a{
        color:#fff;
        padding:0 50px;
        font-size: 16px;
    }
    .foot .tips{
        width: 100%;
        text-align: center;
        font-size: 14px;
        margin-bottom:30px;
    }
    .foot .check{
        margin-top: 70px;
        width: 100%;
        font-size: 14px;
        margin-bottom: 30px;
        text-align: center;
    }
    .foot .check a{
        padding-left:3px;
    }
</style>
