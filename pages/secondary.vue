<template>
    <div class="wrap">
        <secondHeader></secondHeader>
        <div class="bott2">
            <div class="bott clearfix">
                <div class="logo1">
                    <a href="/"><img src="../assets/img/logo.png" alt=""></a>
                </div>
                <div class="seconds-nav">
                    <span><a href="#" class="active">在售</a></span>
                    <span><a href="#">小区</a></span>
                    <span><a href="#">地图找房</a></span>
                    <span><a href="#">计算器</a></span>
                    <span><a href="#">去估价</a></span>
                </div>
            </div>
        </div>
        <!--搜索框-->
        <search></search>
        <!--搜索框结束-->

        <!--筛选盒子-->
        <div class="filter-box">
            <filterBox>
                <template>
                    <div class="filter clearfix">
                        <span class="title">
                            区域
                        </span>
                        <div>
                            <el-checkbox v-model="isChecked.r_id" class="fll" @click="handleClear('r_id')">
                                不限
                            </el-checkbox>
                            <el-checkbox-group v-model="formData.r_id" @change="handleChange('r_id')">
                                <el-checkbox v-for="item in fillData2.r_idData" :label="item" :key="item.value">
                                    {{item.title}}
                                </el-checkbox>
                            </el-checkbox-group>
                        </div>
                    </div>
                    <div class="price mt-30 clearfix">
                        <span>
                            价格
                        </span>
                        <el-checkbox v-model="isChecked.total_price" class="fll" @change="handleClear('total_price')">
                            不限
                        </el-checkbox>
                        <el-checkbox-group v-model="formData.total_price" @change="handleChange('total_price')">
                            <el-checkbox v-for="item in fillData.total_priceData" :label="item" :key="item.value">
                                {{item.title}}
                            </el-checkbox>
                        </el-checkbox-group>
                    </div>
                </template>
            </filterBox>
        </div>
        <rightBox></rightBox>
        <MyFooter></MyFooter>
    </div>
</template>

<script>
    import axios from '~/plugins/axios'
    import api from '~/mainApi/index'
    import secondHeader from '~/components/second-header.vue'
    import search from '~/components/second-search.vue'
    import rightBox from '~/components/right-box'
    import filterBox from '~/components/filter-box'
    import MyFooter from '~/components/Footer.vue'
    export default {
        name: "secondary",
        head(){
            return{
                title:"福居网二手房"
            }
        },
        async asyncData() {
            let r_idData = await axios.get(api.paramToUrl(api.regionLists, {city: "呼和浩特"}))
            r_idData.data.data = r_idData.data.data.map(item => {
                item.title = item.area;
                return item
            })
            return {
                fillData2: {
                    r_idData: r_idData.data.data
                }
            }
        },
        data(){
            return{
                formData:{
                    r_id: [],
                    total_price: [],
                    bedroom: [],  //户型
                    minPrice: "",
                    maxPrice: "",
                    type: [],
                    decoration: [],
                    direction: [],
                    built_area: [],
                    minCustom_bulit_area: "",
                    maxCustom_bulit_area: "",
                    dianti: [],
                    age: [],
                    floor_type: [],
                    search: ""
                },
                isShow:false,
                fillData:{
                    total_priceData:[
                        {value:'0-30',label:"30万以下"},
                        {value:'30-40',label:"30-40万"},
                        {value:'40-50',label:"40-50万"},
                        {value:'50-99999',label:"50万以上"}
                    ],
                    hourseType:[
                        {value:1,label:"一室"},
                        {value:2,label:"二室"},
                        {value:3,label:"三室"},
                        {value:4,label:"四室"},
                        {value:5,label:"五室"}
                    ],
                    Type:[
                        {value:1,label:"平层"},
                        {value:2,label:"复式"},
                        {value:3,label:"跃层"}
                    ],
                    decorate:[
                        {value:1,label:"毛培"},
                        {value:2,label:"豪装"},
                        {value:3,label:"精装"},
                        {value:4,label:"简装"},
                        {value:5,label:"中装"},
                    ],
                },
                isChecked: {
                    r_id: true,
                    total_price: true,
                    built_area: true,
                    floor_type: true
                },
                selectedObj: {},
                houseCount: 0,
                houseArr: []
            }
        },
        components:{
            secondHeader,
            rightBox,
            search,
            MyFooter,
            filterBox
        },
        directives:{
            trans:{
                update(el,binding,vnode){
                    let isShow = vnode.context.$data.isShow;
                    if(!isShow){
                        el.style.height = 0;
                    }else{
                        el.style.height = "auto";
                        let startHeight = 0;
                        let targetHeight = getComputedStyle(el).height;
                        el.style.transition="none";
                        el.style.height = startHeight;
                        el.offsetWidth;
                        el.style.transition = "height ease .5s";
                        el.style.height = targetHeight;
                    }
                }
            }
        }
    }
</script>

<style>
    .filter el-checkbox-group{
        float:left;
        width: 600px;
    }
</style>
<style scoped>
    .bott2{
        width: 100%;
        border-bottom: 1px solid #ccc;
    }
    .bott2 .bott{
        width: 1100px;
        height: 80px;
        font-size: 16px;
        margin:0 auto;
    }
    .bott2 .bott .logo1{
        float: left;
        padding-top: 20px;
        width: 132px;
    }
    .bott2 .bott .seconds-nav .active{
        color: #c30d23;
    }
    .bott2 .bott .seconds-nav{
        margin-left: 60px;
        margin-top: 5px;
        float: left;
        height: 80px;
    }
    .bott2 .bott .seconds-nav span{
        text-align: center;
        display: table-cell;
        vertical-align: middle;
        padding: 25px;
    }
    .bott2 .bott .seconds-nav span a:hover{
        color:#c30d23;
    }
    /*筛选框*/
    .filter-box{
        width: 1100px;
        margin:30px auto;
    }
    .filter-box span.title{
        font-size: 14px;
        color:#333;
        width: 96px;
        font-weight: 400;
        float: left;
    }
    .filter div{
        width: 800px;
        float: left;
    }
</style>