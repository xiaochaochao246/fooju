<template>
    <div class="topHeader2">
        <div class="topHeader clearfix">
            <div class="nav clearfix">
                <span class="nav-item first"><a href="/" target="_blank">首页</a></span>
                <span class="nav-item"><a href="/secondary" target="_blank">二手房</a></span>
                <span class="nav-item"><a href="/newhouse" target="_blank">新房</a></span>
                <span class="nav-item"><a href="#" target="_blank">租房</a></span>
                <span class="nav-item"><a href="#" target="_blank">学区房</a></span>
                <span class="nav-item"><a href="#" target="_blank">小区</a></span>
                <span class="nav-item"><a href="#" target="_blank">经纪人</a></span>
                <span class="nav-item"><a href="#" target="_blank">百科</a></span>
                <span class="nav-item spinner">
                    <a class="toggle" target="_blank">在线委托</a>
                    <div class="spinner-content">
                        <div><a href="#" target="_blank">我是业主</a></div>
                        <div><a href="#" target="_blank">帮我找房</a></div>
                    </div>
                </span>
                <span class="nav-item"><a href="#" target="_blank">工具</a></span>
                <span class="nav-item"><a href="#" target="_blank">专题</a></span>
            </div>
            <div class="fright clearfix">
                <span class="login" @click="loginbtn"><a href="javascript:">请登录</a></span>
                <span class="register"><a href="/register">立即注册</a></span>
            </div>
        </div>
        <div class="logins" v-if="loginisShow">
            <i class="iconfont icon-guanbi close" @click="closes"></i>
            <loginCom2></loginCom2>
        </div>
    </div>
</template>

<script>
import loginCom2 from '~/components/login.vue'
    export default {
        name: "second-header",
        data(){
            return{
                loginisShow:false
            }
        },
        methods:{
            loginbtn(){
                this.loginisShow = true;
            },
            closes(){
                this.loginisShow = false
            }
        },
        components:{
            loginCom2
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
    .topHeader2{
        width: 100%;
        background-color: #f4f4f4;
    }
    .topHeader{
        width: 1100px;
        margin:0 auto;
    }
    .nav{
        font-size: 16px;
        float: left!important;
        padding-top:10px;
    }
    .nav>.nav-item{
        display: inline-block;
        padding-left:35px;
        cursor: pointer;
    }
    .nav>.nav-item.first{
        padding-left: 0;
    }
    .nav>.nav-item>a{
        padding:10px 0 20px;
        display: inline-block;
        height: 100%;
        border-bottom: 2px solid transparent;
    }
    .nav .spinner{
        position: relative;
    }
    .nav .spinner:hover .spinner-content{
        display: block;
    }
    .nav .spinner .spinner-content a:hover{
        border-bottom: none;
    }
    .nav .spinner .spinner-content{
        position: absolute;
        background-color: #ffffff;
        width: 100%;
        top:50px;
        left: 18px;
        z-index: 998;
        display: none;
    }
    .spinner-content{
        margin-left: 0;
    }
    .spinner-content div{
        width: 100%;
        cursor: pointer;
        text-align: center;
        padding:8px 0;
    }
    .spinner-content div a{
        padding-bottom:5px;
    }
    .nav-item a:hover{
        color:#f00;
        border-bottom: 2px solid #f00;
    }
    .topHeader span.login {
        padding:0 10px 0 10px;
        border-right: 1px solid #333;
    }
    .topHeader span.register{
        padding-left: 10px;
        padding-right: 0;
    }
    a{
        background-color: transparent;
    }
    a,a:hover,a:visited{
        color: #000;
        text-decoration: none;
    }
    .topHeader span.login,.topHeader span.register{
        display: inline-block;
    }
    .topHeader .fright{
        margin-top: 20px;
        float: right;
    }
    .login a,.register a{
        padding:10px 0;
        font-size: 12px;
        color:#333;
    }
</style>