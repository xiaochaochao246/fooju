<template>
    <div class="middle clearfix">
        <div class="content" v-tab style="width: 0;position: relative">
            <slot name="middle">
                <div class="flex-box fll" >
                    <div style="background: red;width: 621px;height: 400px;"></div>
                </div>
            </slot>
            <div class="btn">
               <span v-show="!isShow" @click="handleShow">
                右<i class="iconfont icon-mjiantou"></i>
               </span>
                <span v-show="isShow" @click="handleShow">
                左<i class="iconfont icon-mjiantou-copy"></i>
               </span>
            </div>
        </div>
    </div>

</template>

<script>
    export default {
        name: "leftList",
        data(){
            return{
                isShow:false
            }
        },
        methods:{
            handleShow(){
                this.isShow = !this.isShow;
            }
        },
        directives:{
            tab:{
                update(el,binding,vnode){
                    let isShow = vnode.context.$data.isShow;
                    if (!isShow) {
                        el.style.width = 0;
                    }
                    else{
                        el.style.width = "auto";
                        let startWidth = 0;
                        let targetWidth = getComputedStyle(el).width;
                        el.style.transition = "none";
                        el.style.width = startWidth;
                        el.offsetWidth;
                        el.style.transition = "width ease .5s";
                        el.style.width = targetWidth;
                    }
                }
            }
        }
    }
</script>

<style scoped>
    .middle{
        width: 621px;
    }
    .flex-box{
        transition: width ease 3s;
    }
    .btn{
        position: absolute;
        right: -20px;
        top: 200px;
        width: 20px;
        height: 40px;
        background: #f7f8fb;
        border-radius: 4px;
    }
</style>