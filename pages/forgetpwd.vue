<template>
    <div class="forger">
        <forgerHeader/>
        <div class="content">
            <div style="height:30px;"></div>
            <div class="main_content">
                <div class="top clearfix">
                    <span class="fll">
                        找回密码
                    </span>
                    <a href="/login" class="flr">返回登录</a>
                </div>
                <div class="middle">
                    <form class="loginform">
                        <div class="one">
                            <i class="iconfont icon-z-phone"></i>
                            <input type="tel" name="phone" placeholder="请输入手机号">
                        </div>
                        <div class="phoneErrorMsg">
                            请输入正确的手机号
                        </div>
                        <div class="two">
                            <i class="iconfont icon-mima"></i>
                            <input class="yanzheng" type="text"
                                   placeholder="请输入短信验证码">
                            <button type="button" class="obtain">获取验证码</button>
                        </div>
                        <input type="button" value="下一步">
                    </form>
                </div>
            </div>
            <forgetFooter/>
        </div>
    </div>
</template>
<script>
import forgerHeader from '~/components/users-header'
import forgetFooter from '~/components/users-footer'
export default {
    head(){
            return{
                title:"找回密码"
        }
    },
    components:{
        forgerHeader,
        forgetFooter
    },
}
</script>
<style scoped>
.content{
    width: 100%;
    height: 600px;
    margin:0px auto;
    background-color: #f2f2f2;
}
.content .main_content{
    width: 360px;
    padding:40px 130px;
    margin: 0px auto;
    background: #fff;
}
.main_content .top span{
    font-size: 28px;
    color:#666;
}
.main_content .top a{
    font-size: 14px;
    color:#f90;
    margin-top:16px;
}
.main_content .middle{
    color:#aeaeae;
}
.main_content .middle .one,.main_content .middle .two{
    position: relative;
}
.main_content .middle .one{
    margin-top:35px;
}
.main_content .middle .phoneErrorMsg{
    color:#c30d23;
    margin-top: 20px;
    display: none;
}
.main_content .middle .two{
    margin-top:20px;
}
.main_content .middle .two i{
        position: absolute;
        font-size: 20px;
        top:17px;
        left:50%;
        margin-left: -172px;
    }
.main_content .middle .two input{
        float: left;
        width: 206px;
        height: 50px;
        border: 1px solid #ccc;
        padding-left:30px;
    }
    .main_content .middle .two button{
        width: 110px;
        height: 54px;
        background: 0 0;
        border: 1px solid #ccc;
        float: right;
        text-transform: none;
    }
    .main_content .middle .obtain{
        padding:0;
        line-height: 54px;
        font-size: 14px;
        cursor: pointer;
    }
.main_content .middle .one i{
    position: absolute;
    font-size: 20px;
    top:17px;
    left:50%;
    margin-left:-172px;
}
.main_content .middle .one input{
    width: 328px;
    height: 50px;
    border: 1px solid #ccc;
    padding-left:30px;
    line-height: 50px;
    font-size: 16px;
}
.main_content .middle input[type=button]{
    width: 360px;
    background-color: #c30d23;
    color:#fff;
    text-align: center;
    height: 50px;
    line-height: 50px;
    margin-top:20px;
    border: none;
    cursor: pointer;
}
</style>


