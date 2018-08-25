<template>
    <div class="container">
        <!--头部-->
        <div class="header2">
            <div class="header">
                <div class="top">
                    <span class="login" @click="loginbn">
                        <a href="javascript:">请登录</a>
                    </span>
                    <span class="register">
                        <a href="/register">立即注册</a>
                    </span>
                </div>
                <!--<div class="top">-->
                    <!--<span class="register">退出</span>-->
                <!--</div>-->
                <div class="logins" v-if="loginShow">
                    <i class="iconfont icon-guanbi close" @click="closes"></i>
                    <loginCom></loginCom>
                </div>
                <div class="bottom clearfix">
                    <div class="logo">
                        <a href="#">
                            <img src="../assets/img/logo.png" alt="">
                        </a>
                    </div>
                    <div class="select-city">
                        <span>
                             呼和浩特
                             <i class="iconfont icon-jiantouxia"></i>
                        </span>
                    </div>
                    <div class="nav clearfix">
                        <span class="nav-item active">
                            <a href="/" target="_blank">首页</a>
                        </span>
                        <span class="nav-item">
                            <a href="/secondary" target="_blank">二手房</a>
                        </span>
                        <span class="nav-item">
                            <a href="/newhouse" target="_blank">新房</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">租房</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">学区房</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">小区</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">经纪人</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">百科</a>
                        </span>
                        <span class="nav-item spinner">
                            <a class="toggle" target="_blank">在线委托</a>
                            <div class="spinner-content">
                                <div>
                                    <a href="#" target="_blank">我是业主</a>
                                </div>
                                <div>
                                    <a href="#" target="_blank">帮我找房</a>
                                </div>
                            </div>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">工具</a>
                        </span>
                        <span class="nav-item">
                            <a href="#" target="_blank">专题</a>
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import loginCom from '~/components/login.vue'
    export default {
        name: "index-header",
        data(){
            return{
                loginShow:false,
            }
        },
        methods:{
            closes(){
                this.loginShow=false;
            },
            loginbn(){
                this.loginShow = true;
            }
        },
        components:{
            loginCom
        }
    }
</script>

<style scoped>
.logins{
    padding-top:70px;
    overflow: hidden;
    display: flex;
    position: fixed;
    top:0;
    bottom:0;
    left:0;
    right:0;
    width: 100%;
    height: 100%;
    background:rgba(0,0,0,.3);
    z-index:1000;
}
.logins i{
    position: absolute;
    font-size:30px;
    right:370px;
    top:80px;
}
    .container{
        width:100%;
        /*overflow: hidden;*/
    }
    /*头部*/
    .header2{
        width: 100%;
        height:103px;
        margin:0 auto;
    }
    .header2 .header{
        width: 1100px;
        margin:0 auto;
    }
    .header .top{
        text-align: right;
        font-size: 12px;
        color:#333;
        padding:15px 0 5px;
    }
    .header .top .login{
        border-right: 1px solid #333;
        padding-right: 10px;
    }
    .header .top .login , .header .top .register{
        display: inline-block;
        padding:0 0 0 10px;
    }
    .header .bottom{
        font-size: 16px;
    }
    .header .bottom.clearfix{
        width: 1100px;
        height: 70px;
    }
    .header .bottom .logo{
        width: 128px;
        height:43px;
        margin-top:17px;
    }
    .header .bottom .logo a img{
        width: 128px;
        height:40px;
    }
    .header .botton .select-city{
        padding-top:24px;
    }
    .bottom>div{
        float: left;
    }
    .bottom .select-city span{
        display: inline-block;
        font-size: 16px;
        padding:4px 10px;
        margin-left: 20px;
        border-radius:15px;
        border:1px solid #999;
        color:#333;
        position: relative;
        top:25px;
    }
    .header .bottom .nav{
        float: right;
        padding-top:30px;
    }
    .header .bottom .nav .nav-item a{
        padding-bottom:19px;
    }
    .nav-item.active a{
        color:#f00;
        border-bottom: 2px solid #f00;
    }
    .header .bottom .nav>.nav-item{
        cursor: pointer;
        display: inline-block;
        padding-left: 35px;
    }
    .nav-item a:hover{
        color:#f00;
        border-bottom: 2px solid #f00;
    }
    .spinner {
        position: relative;
    }
    .spinner .spinner-content{
        width: 125px;
        position: absolute;
        left: 5px;
        top: 40px;
        background:#fff;
        display: none;
        z-index:9999;
    }
    .spinner:hover .spinner-content{
        display: block;
    }
    .spinner-content div a{
        padding-bottom:5px;
    }
    .spinner-content div a:hover{
        border-bottom: none;
    }
    .spinner .spinner-content div{
        width: 100%;
        cursor: pointer;
        text-align: center;
        padding:10px 0;
    }
</style>