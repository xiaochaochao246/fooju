<template>
    <div class="wrap">
        <div class="header">
            <secondHeader></secondHeader>
            <div class="bottom clearfix">
                <div class="logo">
                    <a href="/"><img src="../assets/img/logo.png" alt=""></a>
                </div>
                <div class="select-city">
                    <span>
                        呼和浩特
                        <i class="iconfont icon-jiantouxia"></i>
                    </span>
                </div>
                <div class="second-nav active">
                    <a href="/">首页</a>
                </div>
                <div class="second-nav">
                    <a href="">楼盘</a>
                </div>
                <div class="search">
                    <div class="fright clearfix">
                        <input type="text" class="fleft searchInput">
                        <div class="searchBtn fleft">搜索</div>
                        <div class="mapSearch fleft">地图找房</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="top-banner">
            <div v-banner  style="overflow: hidden;" class="banner">
                <div class="swiper-wrapper" style="height: 100%;overflow: hidden;">
                    <div class="swiper-slide" style="height: 100%;overflow: hidden;"
                         v-for="banner in bannerData" :key="banner.id">
                        <img class="mypicture" :src="'http://www.fooju.cn/'+banner.picurl">
                    </div>
                </div>
                <div class="filter">
                    <div class="select">
                        <ul class="main_box">
                            <li class="select_box" id="more">
                            <span>
                                区域
                                <i class="iconfont icon-jiantouxia"></i>
                            </span>
                                <ul class="region son_ul" id="nav-ul">
                                    <li>不限</li>
                                    <li>金桥开发区</li>
                                    <li>如意开发区</li>
                                    <li>玉泉区</li>
                                    <li>回民区</li>
                                    <li>赛罕区</li>
                                    <li>新城区</li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                    <div class="select">
                        <ul class="main_box">
                            <li class="select_box">
                            <span>
                                类型
                                <i class="iconfont icon-jiantouxia"></i>
                            </span>
                                <ul class="region son_ul">
                                    <li>不限</li>
                                    <li>金桥开发区</li>
                                    <li>如意开发区</li>
                                    <li>玉泉区</li>
                                    <li>回民区</li>
                                    <li>赛罕区</li>
                                    <li>新城区</li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                    <div class="select">
                        <ul class="main_box">
                            <li class="select_box">
                            <span>
                                房屋属性
                                <i class="iconfont icon-jiantouxia"></i>
                            </span>
                                <ul class="region son_ul">
                                    <li>不限</li>
                                    <li>金桥开发区</li>
                                    <li>如意开发区</li>
                                    <li>玉泉区</li>
                                    <li>回民区</li>
                                    <li>赛罕区</li>
                                    <li>新城区</li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                    <div class="select">
                        <ul class="main_box">
                            <li class="select_box">
                            <span>
                                均价
                                <i class="iconfont icon-jiantouxia"></i>
                            </span>
                                <ul class="region son_ul">
                                    <li>不限</li>
                                    <li>金桥开发区</li>
                                    <li>如意开发区</li>
                                    <li>玉泉区</li>
                                    <li>回民区</li>
                                    <li>赛罕区</li>
                                    <li>新城区</li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                    <div class="btns">
                        筛选
                    </div>
                </div>
            </div>
        </div>
        <!--新房推荐及广告-->
        <div class="content">
            <!--通栏广告-->
            <div class="leaderboard">
                <div style="position: relative;cursor: pointer;" href="adData[0].ad_url">
                    <img :src="'http://www.fooju.cn/'+adData[0].picurl" alt="" width="100%" height="110">
                    <a href="adData[0].ad_url" style="height: 100%;position: absolute;top:0;
left:0;display: inline-block;z-index: 2;width: 100%;"></a>
                </div>
                <div style="position: relative" href="adData[1].ad_url">
                    <object
                            width="100%" height="110" align="center">
                        <param name="movie" :value="'http://www.fooju.cn/'+adData[1].picurl">
                        <param name="quality" value="high">
                        <param name="play" value="1">
                        <param name="AllowScriptAccess" value="never">
                        <param name="wmode" value="opaque">
                        <embed :src="'http://www.fooju.cn/'+adData[1].picurl" width="100%" height="110"
                               align="center" autostart="true" quality="high" wmode="opaque"
                               pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash">
                    </object>
                    <a href="adData[1].ad_url" style="height: 100%;position: absolute;top:0;
left:0;display: inline-block;z-index: 2;width: 100%;"></a>
                </div>
            </div>
            <!--新房推荐-->
            <div class="house-common">
                <div class="top clearfix" style="display: none">
                    <div class="title fleft">推荐楼盘</div>
                </div>
                <div class="house-tagLine" style="display: none">
                    在售楼盘
                    <span class="salelingNum">6</span>
                </div>
                <div class="housestop">
                    <div class="houses clearfix">
                        <div class="house fleft" v-for="house in houseData" :key="house.id">
                            <div class="house-img">
                                <a href="#">
                                    <img :src="'http://www.fooju.cn/'+house.pic[0].pic" alt="">
                                </a>
                                <div class="bottom-content">
                                    <div class="house-name">{{house.title}}</div>
                                    <div class="addr">{{house.address}}</div>
                                </div>
                            </div>
                            <div class="tags clearfix">

                            </div>
                            <div class="bottoms">
                                <div class="house-feature clearfix">
                                    <div class="fleft">
                                        均价：
                                        <span class="price">
                                            {{house.average_price}}元/平
                                        </span>
                                    </div>
                                    <div class="fright house-type">
                                        {{house.building_type}}
                                    </div>
                                </div>
                                <div class="spec">
                                    建筑面积{{house.built_area}}㎡
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <rightBox></rightBox>
        <MyFooter></MyFooter>
    </div>
</template>

<script>
    import axios from '~/plugins/axios'
    import api from '~/mainApi/index'
    import secondHeader from '~/components/second-header.vue'
    import rightBox from '~/components/right-box'
    import MyFooter from '~/components/Footer.vue'
    export default {
        name: "newhouse",

        async asyncData (){
            let bannerData = await axios.get(api.paramToUrl(api.adLists,{type:0,position:1}));
            let adData = await axios.get(api.paramToUrl(api.indexLeaderboard,{position:1,platform:1}));
            let houseData = await axios.get(api.paramToUrl(api.recommendNew,{page_size:6,page_num:1}));
            //console.log(houseData.data);
            return{
                bannerData:bannerData.data.data,
                adData:adData.data.datas.top,
                houseData:houseData.data.data
            }
        },
        // mounted(){
        //      console.log(this.houseData)
        // },
        components:{
            secondHeader,
            rightBox,
            MyFooter
        },
        directives:{
            banner(el,binding,vnode){
                function setBannerHeight() {
                    let bannerHeight = (document.documentElement.clientHeight ||
                        document.body.clientHeight)-103;
                    let bannerWidth = document.documentElement.clientWidth ||
                        document.body.clientWidth;
                    el.style.width = bannerWidth+"px";
                    el.style.height = bannerHeight+"px";
                    let bannerRate = bannerWidth/bannerHeight;
                    let imgArr = el.querySelectorAll("img");
                    imgArr.forEach(item=>{
                        let imgHeight = item.offsetHeight;
                        let imgWidth = item.offsetWidth;
                        let imgRate = imgWidth/imgHeight;
                        if(bannerRate>imgRate){
                            item.style.width = "auto";
                            item.style.width = bannerWidth+"px";
                            item.style.height = "auto";
                            item.style.marginTop = -(item.offsetHeight-bannerHeight)/2+"px";
                        }else{
                            item.style.height = bannerHeight+"px";
                            item.style.marginLeft = -(item.offsetWidth-bannerWidth)/2+"px";
                        }
                    })
                }
                setBannerHeight();
                window.onresize = setBannerHeight
            },
        },
    }
</script>

<style>
    .mypicture{
        display: block;
        width: 100%;
    }
</style>

<style scoped>
    .header{
        width: 100%;
    }
    .header .bottom{
        width: 1100px;
        margin: 0 auto;
        display: table;
        height: 80px;
    }
    .header .bottom .logo{
        width: 132px;
    }
    .header .bottom>div{
        font-size: 16px;
        display: table-cell;
        vertical-align: middle;
    }
    .select-city{
        width: 210px;
        cursor: pointer;
        position: relative;
    }
    .select-city>span{
        font-size: 16px;
        padding:4px 10px !important;
        margin-left: 20px;
        color:#333;
        border-radius: 20px;
        border: 1px solid #999;
    }
    .header .second-nav.active a{
        color:#f00;
    }
    .header .bottom .search{
        width: 600px;
    }
    .header .bottom .search input{
        width: 300px;
        height: 40px;
        padding:0;
        box-sizing: border-box;
    }
    .header .bottom .searchBtn{
        padding:0 35px;
        background-color: #c30d23;
        margin-right: 20px;
        height: 40px;
        line-height: 40px;
        color:#fff;
    }
    .header .bottom .mapSearch{
        height: 40px;
        line-height: 40px;
        padding:0 45px;
        color:#fff;
        cursor: pointer;
        background-color: #5f1985;
    }
    .fleft{
        float: left;
    }
    .fright{
        float: right;
    }
    /*banner部分开始*/
    .banner{
        position: relative;
    }
    .top-banner{
        width:100%;
        overflow: hidden;
    }
    .top-banner .filter{
        z-index:100;
        position: absolute;
        top:0;
        left: 125px;
        vertical-align: middle;
        display: inline-block;
        height: 100%;
        width: 300px;
        text-align: center;
        background: rgba(255,0,0,0.4);
        padding-top:30px;
    }
    .top-banner .btns{
        margin:50px auto;
        width: 200px;
        height: 50px;
        background-color: #fff;
        color:#000;
        border-radius: 5px;
        text-align: center;
        line-height: 50px;
    }
    .select>ul{
        position: relative;
    }
    .select>ul span i{
        position: absolute;
        right:10px;
        top:3px;
        color:#fff;
    }
    .select_box{
        width: 198px;
        border: 1px solid #ccc;
        position: relative;
        margin-left: 49px;
        color:#fff;
        margin-top: 50px;
        border-radius: 3px;
    }
    .select_box ul li{
        cursor: pointer;
    }
    .son_ul li{
        display: block;
        line-height: 25px;
        width: 196px;
    }
    .select_box span{
        position: relative;
        cursor: pointer;
        display: block;
        line-height: 25px;
        width: 198px;
        height: 25px;
        overflow: hidden;
    }
    .son_ul{
        /*display: none;*/
        width: 196px;
        position: absolute;
        left: 0;
        top:25px;
        border: 1px solid #ccc;
        background-color: #fff;
        z-index:2;
        color:#333;
    }
    .son_ul li{
        display: block;
        line-height: 25px;
        width: 196px;
    }
    ul li{
        list-style-type: none;
    }
    /*新房推荐及广告*/
    .content{
        width: 1100px;
        margin:0 auto;
    }
    .content .leaderboard{
        width: 100%;
        margin:80px 0;
    }
    /*新房推荐*/
    .content .house-common{
        margin-bottom: 80px;
        width: 100%;
    }
    .house-common .top{
        margin-bottom:20px;
    }
    .house-common .top .title{
        font-size: 30px;
        font-weight: bolder;
        color:#333;
    }
    .house-common .house-tagLine{
        margin-bottom:40px;
        color:#666;
    }
    .house-common .salelingNum{
        color:#c30d23;
    }
    .house-common .houses> :first-child.house{
        margin-left: 0;
    }
    .house-common .houses> :nth-child(4).house{
        margin-left: 0;
    }
    .house-common .houses .house{
        position: relative;
        margin-left: 37px;
        margin-bottom:40px;
    }
    .house-common .houses .house .house-img{
        width: 342px;
        height: 256px;
        overflow: hidden;
        position: relative;
    }
    .house-common .houses .house .house-img a img{
        width: 342px;
        height: 256px;
        transition: all 2s;
    }
    .house-common .houses .house .house-img a img:hover{
        transform: scale(1.1);
    }
    .house-common .houses .house .bottom-content{
        position: absolute;
        left: 0;
        bottom:0;
        width: 100%;
        color:#fff;
        box-sizing: border-box;
        padding:5px 10px;
        font-size: 16px;
        background: rgba(0,0,0,.5);
    }
    .house-common .house-name{
        margin-bottom: 10px;
        font-weight: bolder;
        font-size: 20px;
    }
    .house-common .houses .house .tags{
        position: absolute;
        top:0;
        left:0;
        z-index: 2;
        width: 100%;
        font-size: 14px;
        color: #fff;
    }
    .house-common .house-feature{
        color:#666;
        font-size: 16px!important;
        margin:20px 0 10px;
    }
    .house-common .house-feature> :first-child{
        padding-top:5px;
    }
    .house-common .house-feature .house-type{
        padding:5px;
        background: rgba(153,153,153,.2);
        border-radius: 2px;
        max-width: 187px;
        font-size: 14px;
        text-align: center;
    }
    .house-common .spec{
        font-size: 14px;
        color:#666;
    }
    .house-common .houses .house .bottoms .house-feature .price{
        color:#c30d23;
    }
</style>