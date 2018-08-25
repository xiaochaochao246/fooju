<template>
        <div class="main_content">
                <div class="top clearfix">
                    <span class="fll">
                        登录
                    </span>
                    <a href="/register" class="flr">没有账号，立即注册</a>
                </div>
                <div class="middle">
                    <form class="loginform">
                        <div class="one">
                            <i class="iconfont icon-z-phone"></i>
                            <input type="tel" name="mobile" v-model="formData.mobile" placeholder="请输入手机号">
                        </div>
                        <div class="two">
                            <i class="iconfont icon-mima"></i>
                            <input type="password" name="pwd" v-model="formData.password" placeholder="请输入密码">
                        </div>
                        <div class="three" @click="submit">
                            登录
                        </div>
                        <a href="/forgetpwd" class="four">
                            忘记密码？
                        </a>
                    </form>
                    <div class="five clearfix">
                        <a href="" class="fll">
                            <img src="../assets/img/qq.png" alt="">
                            <br>
                            <span>qq登录</span>
                        </a>
                        <a href="" class="fll">
                            <img src="../assets/img/weixin.png" alt="">
                            <br>
                            <span>微信登录</span>
                        </a>
                        <a href="" class="fll">
                            <img src="../assets/img/weibo.png" alt="">
                            <br>
                            <span>微博登录</span>
                        </a>
                    </div>
                </div>
            </div>
</template>
<script>
import axios from '~/plugins/axios'
import api from '~/mainApi/index'
import md5 from 'md5'
import qs from 'qs'
export default {
    data(){
        return{
            formData:{
                mobile:"",
                password:""
            }
        }
    },
    methods:{
        submit(){
            let params = {
                password:md5(md5(this.formData.password))+"fojuwang",
                mobile:this.formData.mobile
            }
            axios.post("/api.php?s=Login/login",params).then(res=>{
                console.log(res);
                this.$router.push({path:'/'});
            }).catch(err=>{
                console.log(err);
            })
        }
    },
}
</script>
<style scoped>
.main_content{
    width: 360px;
    height:400px;
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
.main_content .middle .two{
    margin-top:20px;
}
.main_content .middle .one i,.main_content .middle .two i{
    position: absolute;
    font-size: 20px;
    top:17px;
    left:50%;
    margin-left:-172px;
}
.main_content .middle .one input,.main_content .middle .two input{
    width: 328px;
    height: 50px;
    border: 1px solid #ccc;
    padding-left:30px;
    line-height: 50px;
    font-size: 16px;
}
.main_content .middle .three{
    width: 360px;
    height: 50px;
    color:#fff;
    background-color: #c30d23;
    line-height: 50px;
    text-align: center;
    border:none;
    font-size: 16px;
    cursor: pointer;
    margin-top:20px;
}
.main_content .middle .four{
    margin-top:30px;
    color:#666;
    text-align: center;
    padding-bottom:20px;
    display: block;
    font-size: 14px;
}
.main_content .middle .five{
    text-align: center;
    width: 300px;
    margin:0 auto;
    font-size: 14px;
    color:#666;
}
.main_content .middle .five a{
    width: 60px;
    text-align: center;
    margin: 0 20px;
}
.main_content .middle .five a img{
    width: 40px;
    height: 40px;
    margin-bottom: 6px;
}
</style>


