<template>
    <div class="login">
        <loginHeader></loginHeader>
        <div class="content">
            <div style="height:30px;"></div>
            <login/>
            <loginfooter/>
        </div>
    </div>
</template>
<script>
import login from '~/components/login'
import loginHeader from '~/components/users-header'
import loginfooter from '~/components/users-footer'
export default {
    head() {
        return {
            title: "福居网登录"
        }
    },
    components:{
        loginHeader,
        login,
        loginfooter
    }
}
</script>
<style scoped>
.content{
    width: 100%;
    height: 600px;
    margin:0 auto;
    background-color: #f2f2f2;
}
</style>


