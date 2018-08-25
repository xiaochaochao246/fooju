<template>
    <div class="wrap">
        <userHeader></userHeader>
        <div class="conte">
            <div style="height: 1px;"></div>
            <div class="con">
                <div class="conHead">
                    <div content="conCreat">
                        <span class="cleft">创建账号</span>
                        <a href="/login" class="cright">已有账号，立即登录</a>
                    </div>
                    <form id="register" @submit.prevent>
                        <div class="one">
                            <i class="iconfont icon-z-phone"></i>
                            <input type="tel" name="phone" placeholder="请输入手机号"
                                   v-model="formData.mobile" autofocus="true" @keyup="testMobile">
                        </div>
                        <div class="phoneErrorMsg" v-text="phoneError" v-show="phoneError">
                            请输入正确的手机号
                        </div>
                        <div class="two">
                            <i class="iconfont icon-mima"></i>
                            <input class="yanzheng" type="text" v-model="formData.verify"
                                   placeholder="请输入短信验证码">
                            <button type="button" class="obtain" :disabled="canSend" v-text="btnText"
                                    @click="sendVerify"></button>
                        </div>
                        <div class="yzmErrorMsg clearfix" v-text="smsError" v-show="smsError">
                            验证码输入错误
                        </div>
                        <div class="three">
                            <i class="iconfont icon-mima"></i>
                            <input type="password" name="password" v-model="formData.password" @keyup="testPwd"
                                   placeholder="请输入6-18位密码">
                        </div>
                        <div class="passErrorMsg" v-text="pwdError" v-show="pwdError">密码格式不正确</div>
                        <div class="four">
                            <i class="iconfont icon-nicheng"></i>
                            <input type="text" name="username" v-model="formData.name" @keyup="testName"
                                   placeholder="请输入昵称">
                        </div>
                        <div class="passErrorMsg" v-text="nameError" v-show="nameError">昵称格式不正确</div>
                        <input type="button" value="立即注册" @click="submit">
                    </form>
                    <div class="five clearfix">
                        <span class="fleft">点击立即注册，则表示您阅读并同意遵守</span>
                        <a href="#" class="fleft">福居网平台服务协议</a>
                    </div>
                </div>
                <userFooter></userFooter>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from '~/plugins/axios'
    import api from '~/mainApi/index'
    import userFooter from '~/components/users-footer.vue'
    import userHeader from '~/components/users-header.vue'
    import md5 from 'md5'
    import qs from 'qs'
    export default {
        name: "register",
        data(){
            return{
                formData:{
                    mobile:"",
                    verify:"",
                    password:"",
                    name:""
                },
                btnText:"获取验证码",
                isSending:false,
                canCommit:false,
                phoneError:"",
                smsError:"",
                pwdError:"",
                nameError:""
            }
        },
        methods:{
            testMobile(){
                let mobileReg = /((13[0-9])|(14[5,7])|(15[0-3,5-9])|(17[0,3,5-8])|(18[0-9])|166|198|199|(147))\d{8}$/
                this.phoneError = mobileReg.test(this.formData.mobile)? "" : "请输入正确的手机号码";
                return mobileReg.test(this.formData.mobile)
            },
            sendVerify(){
                if(this.testMobile()){
                    axios.get(`/api.php?s=Msg/send_msg/mobile/${this.formData.mobile}`).then(res=>{
                        this.send()
                    }).catch(err=>{
                        alert(err)
                    })
                }
            },
            send(){
                this.isSending = true;
                let time = 60;
                this.btnText = time + "s";
                let timer = setInterval(()=>{
                    time--;
                    this.btnText = time + "s";
                    if(time<=0){
                        clearInterval(timer)
                        this.btnText = "重新获取";
                        this.isSending = false;
                    }
                },1000)
            },
            testPwd(){
                let pwdReg = /^.{6,18}$/;
                this.pwdError = pwdReg.test(this.formData.password) ? "" : "请输入6-18位密码"
            },
            testName() {
                let nameReg = /^.{1,20}$/;
                this.nameError = nameReg.test(this.formData.name)? "" : "请输入1到20个字符作为您的昵称"
            },
            submit(){
                if(this.phoneError || this.nameError || this.pwdError || this.formData.verify.length<4){
                    return
                }
                axios.get(`/api.php?s=Msg/verify/mobile/${this.formData.mobile}/verify/${this.formData.verify}`)
                    .then(res=>{
                        console.log(res.code);
                        if(res.data.code!=200){
                            this.smsError=res.data.msg;
                        }else{
                            let params = {
                                password:md5(md5(this.formData.password))+"fojuwang",
                                mobile: this.formData.mobile,
                                name: this.formData.name
                            };
                            axios.post("/api.php?s=Login/register",params).then(res=>{
                                console.log(res)
                            }).catch(error=>{
                                console.log(error)
                            })
                        }
                    }).catch(err=>{
                        console.log(err)
                })
            }
        },
        head(){
            return{
                title:"福居网注册"
            }
        },
        components:{
            userFooter,
            userHeader
        },
        computed:{
            canSend(){
                let mobile = this.formData.mobile;
                let mobileReg = /((13[0-9])|(14[5,7])|(15[0-3,5-9])|(17[0,3,5-8])|(18[0-9])|166|198|199|(147))\d{8}$/
                if(mobileReg.test(mobile)&& !this.isSending){
                    return false
                }else{
                    return true;
                }
            }
        }
    }
</script>

<style scoped>
    /*content*/
    .conte{
        background-color: #f2f2f2;
    }
    .conte .con{
        width: 1100px;
        margin:30px auto;
    }
    .conte .con .conHead{
        width: 360px;
        height: auto;
        padding:40px 130px;
        margin:30px auto;
        background-color: #fff;
    }
    .con .conHead .cleft{
        font-size: 28px;
        color:#666;
    }
    .con .conHead .cright{
        float:right;
        font-size: 14px;
        color:#f90;
        margin-top: 16px;
    }
    #register{
        height: 100%;
    }
    #register .one{
        position: relative;
        margin-top:35px;
    }
    #register .one i{
        font-size: 20px;
        position: absolute;
        top:30%;
        left:10px;
    }
    #register .one input,#register .three input,#register .four input{
        width: 328px;
        height: 50px;
        padding-left:30px;
        border: 1px solid #ccc;
    }
    #register .three input,#register .four input{
        margin-top:20px;
    }
    #register .four i{
        font-size: 20px;
        position: absolute;
        top:37px;
        left:10px;
    }
    #register .three i{
        font-size: 20px;
        position: absolute;
        top:37px;
        left:10px;
    }
    #register .phoneErrorMsg,#register .passErrorMsg, .yzmErrorMsg{
        color:#c30d23;
        margin-top: 20px;
    }
    #register .two{
        position: relative;
        margin-top:20px;
    }
    #register .three,#register .four{
        clear:both;
        position: relative;
        margin:0;
    }
    #register .two i{
        position: absolute;
        font-size: 20px;
        top:17px;
        left:50%;
        margin-left: -172px;
    }
    #register .two input{
        float: left;
        width: 206px;
        height: 50px;
        border: 1px solid #ccc;
        padding-left:30px;
    }
    #register .two button{
        width: 110px;
        height: 54px;
        background: 0 0;
        border: 1px solid #ccc;
        float: right;
        text-transform: none;
    }
    #register .obtain{
        cursor: pointer;
        padding:0;
        line-height: 54px;
        font-size: 14px;
    }
    #register input[type=button]{
        width: 360px;
        background-color: #c30d23;
        color: #fff;
        text-align: center;
        height: 50px;
        line-height: 50px;
        border: none;
        margin-top: 20px;
        cursor: pointer;
    }
    .con .conHead .five{
        font-size: 13px;
        color:#666;
        margin-top: 30px;
    }
    .con .conHead .five .fleft{
        float: left;
    }
    .con .conHead .five a{
        font-weight: 700;
    }
</style>