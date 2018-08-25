<template>
    <div class="transitionBox"  v-tab>
        <div class="default-box clearfix">
            <slot>
            </slot>
        </div>
        <div class="transition-middle">
            <div class="box clearfix" style="height: 0" id="middle-box">
                <slot name="middle">
                </slot>
            </div>
        </div>
        <slot name="bottom">
            <h3>最底下的内容</h3>
        </slot>

        <div class="tab-wrap">
            <span v-show="!showMore"  class="flex-btn" id="more" @click="handleShow(true)">更多选项 <i class="iconfont icon-jiantouxia"></i></span>
            <span v-show="showMore"  class="flex-btn" id="retract" @click="handleShow(false)">收起选项 <i class="iconfont icon-jiantoushang"></i></span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "transitionBox",
        data() {
            return {
                showMore: false
            }
        },
        directives: {
            tab: {
                inserted(el,binding,vnode){
                    let moreBtn = el.querySelector("#more");
                    let retractBtn = el.querySelector("#retract");
                    let box = el.querySelector("#middle-box");

                    moreBtn.onclick = function() {
                        console.log(1);
                        if(!window.getComputedStyle){
                            return
                        }
                        box.style.height = "auto";
                        let targetHeight = getComputedStyle(box).height;
                        box.style.height = "0px";
                        box.offsetHeight; //触发浏览器重排
                        box.style.height = targetHeight;
                    };
                    retractBtn.onclick = function() {
                        console.log(2);

                        if(!window.getComputedStyle){
                            return
                        }
                        box.style.height = 0;
                    }

                }
            }
        },
        methods: {
            handleShow(isShow) {
                this.showMore = isShow;
            }
        }
    }
</script>

<style scoped>
    .box {
        transition: height ease .5s;
        overflow: hidden;
    }
    .flex-btn {
        display: block;
        text-align: center;
        font-size: 16px;
        color: #bbb;
        padding: 30px 0;
        border-bottom: 1px solid #ccc;
    }
</style>