<template>
    <div class="wrap">
        <Header></Header>
        <div class="lunbo">
            <div v-banner  style="overflow: hidden;" class="banner" v-swiper:mySwiper="swiperOption">
                <div class="swiper-wrapper" style="height: 100%;overflow: hidden;">
                    <div class="swiper-slide" style="height: 100%;overflow: hidden;"
                         v-for="banner in bannerData" :key="banner.id">
                        <img :src="'http://www.fooju.cn/'+banner.picurl" class="mypicture">
                    </div>
                </div>
            </div>
            <div class="mask" style="z-index:99;" v-banner></div>
        </div>
        <div class="index-container">
            <div class="search">
                <ul class="clearfix links">
                    <li class="fll link-item" :class="{active:selectIndex==0}" @click="selectIndex=0">找二手房</li>
                    <li class="fll link-item" :class="{active:selectIndex==1}" @click="selectIndex=1">找新房</li>
                    <li class="fll link-item" :class="{active:selectIndex==2}" @click="selectIndex=2">找租房</li>
                    <li class="fll link-item" :class="{active:selectIndex==3}" @click="selectIndex=3">找学区房</li>
                    <li class="fll link-item" :class="{active:selectIndex==4}" @click="selectIndex=4">找小区</li>
                </ul>
                <div class="search-button clearfix">
                    <input type="text" class="fll" :placeholder="placeholderText">
                    <span class="search-btn fll">搜索</span>
                </div>
            </div>
            <div class="map-btn">
                <a href="#" target="_blank">
                    <img src="../assets/img/mapSearch.png" alt="">
                    地图找房
                </a>
            </div>
        </div>
        <div class="content">
            <!--头部广告-->
            <div class="top-btngroup" >
                <div class="btn">
                    <a href="#" target="_blank">
                        <img src="../assets/img/store.png" alt="">
                        <div class="title">查门店</div>
                        <div class="text">
                            查优质门店
                        </div>
                    </a>
                </div>
                <div class="btn">
                    <a href="#" target="_blank">
                        <img src="../assets/img/entrust.png" alt="">
                        <div class="title">在线委托</div>
                        <div class="text">
                            有问题我们帮你
                        </div>
                    </a>
                </div>
                <div class="btn">
                    <a href="#" target="_blank">
                        <img src="../assets/img/mapBlue.png" alt="">
                        <div class="title">地图找房</div>
                        <div class="text">
                            地图找房
                        </div>
                    </a>
                </div>
                <div class="btn">
                    <a href="#" target="_blank">
                        <img src="../assets/img/encyclopedias.png" alt="">
                        <div class="title">福居百科</div>
                        <div class="text">
                            看百科了解更多
                        </div>
                    </a>
                </div>
            </div>
            <!--特色-->
            <div class="features clearfix">
                <div class="feature">
                    <a href="#" target="_blank">
                        <img src="../assets/img/3.png" alt="">
                        <div class="featureText">{{advisData[0].title}}</div>
                    </a>
                </div>
                <div class="feature second">
                    <a href="#" target="_blank">
                        <img src="../assets/img/2.png" alt="">
                        <div class="featureText">{{advisData[1].title}}</div>
                    </a>
                </div>
                <div class="feature">
                    <a href="#" target="_blank">
                        <img src="../assets/img/1.png" alt="">
                        <div class="featureText">{{advisData[2].title}}</div>
                    </a>
                </div>
            </div>
            <!--精品新房-->
            <div class="newHouse house-common">
                <div class="top clearfix">
                    <div class="title fleft">精品新房</div>
                    <div class="more fright">
                        <a href="#" target="_blank">
                            更多新房
                            <i class="iconfont icon-mjiantou"></i>
                        </a>
                    </div>
                </div>
                <div class="house-tagLine">在这里为你寻觅一个新家</div>
                <div class="houses clearfix">
                    <div class="house fleft">
                        <div class="house-img">
                            <a href="#" target="_blank">
                                <img :src="'http://www.fooju.cn/'+newHouseData[0].pic" alt="">
                            </a>
                        </div>
                        <div class="tags clearfix">

                        </div>
                        <div class="bottom-content clearfix">
                            <div class="name fleft">
                                {{newHouseData[0].title}}
                            </div>
                            <div class="price fright">{{newHouseData[0].average_price}}元/平</div>
                        </div>
                    </div>
                    <div class="house fleft">
                        <div class="house-img">
                            <a href="#" target="_blank">
                                <img :src="'http://www.fooju.cn/'+newHouseData[1].pic" alt="">
                            </a>
                        </div>
                        <div class="tags clearfix">

                        </div>
                        <div class="bottom-content clearfix">
                            <div class="name fleft">
                                {{newHouseData[1].title}}
                            </div>
                            <div class="price fright">{{newHouseData[1].average_price}}元/平</div>
                        </div>
                    </div>
                    <div class="house fleft">
                        <div class="house-img">
                            <a href="#" target="_blank">
                                <img :src="'http://www.fooju.cn/'+newHouseData[2].pic" alt="">
                            </a>
                        </div>
                        <div class="tags clearfix">

                        </div>
                        <div class="bottom-content clearfix">
                            <div class="name fleft">
                                {{newHouseData[2].title}}
                            </div>
                            <div class="price fright">{{newHouseData[2].average_price}}元/平</div>
                        </div>
                    </div>
                </div>
            </div>
            <!--二手优品-->
            <div class="newHouse house-common">
                <div class="top clearfix">
                    <div class="title fleft">二手优品</div>
                    <div class="more fright">
                        <a href="#" target="_blank">
                            更多二手房
                            <i class="iconfont icon-mjiantou"></i>
                        </a>
                    </div>
                </div>
                <div class="house-tagLine">生活因为宽广，才会不断延伸</div>
                <div class="houses clearfix">
                    <div class="house fleft" v-for="secondData in secondUsedData" :key="secondData.id">
                        <div class="house-img">
                            <a href="#" target="_blank">
                                <img :src="'http://www.fooju.cn/'+secondData.pic" alt="">
                            </a>
                        </div>
                        <div class="price-tag">
                            {{secondData.total_price}}万
                        </div>
                        <div class="bottom">
                            <div class="addr-name">
                                <span class="name">{{secondData.title}}</span>
                            </div>
                            <div class="house-feature clearfix">
                                <div class="house-feature fleft">
                                    <span>{{secondData.bedroom}}室{{secondData.livingroom}}厅{{secondData.wc}}卫</span>
                                    <span>{{secondData.built_area}}㎡</span>
                                    <span></span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!--精品租房-->
            <div class="newHouse house-common">
                <div class="top clearfix">
                    <div class="title fleft">精品租房</div>
                    <div class="more fright">
                        <a href="#" target="_blank">
                            更多租房
                            <i class="iconfont icon-mjiantou"></i>
                        </a>
                    </div>
                </div>
                <div class="house-tagLine">与其等待，不如坐享繁华</div>
                <div class="houses clearfix">
                    <div class="house fleft" v-for="retal in retalData" :key="retal.id">
                        <div class="house-img">
                            <a href="#" target="_blank">
                                <img :src="'http://www.fooju.cn/'+retal.pic" alt="">
                            </a>
                        </div>
                        <div class="bottom">
                            <div class="addr-name">
                                <span class="name">{{retal.title}}</span>
                            </div>
                            <div class="house-feature clearfix">
                                <div class="house-feature fleft">
                                    <span>{{retal.bedroom}}室{{retal.livingroom}}厅{{retal.wc}}卫</span>
                                    <span>{{retal.built_area}}㎡</span>
                                    <span class="price-prices">{{retal.rent}}{{retal.rent_type}}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <rightBox></rightBox>
        <MyFooter/>
    </div>
</template>

<script>
import axios from '~/plugins/axios'
import api from '~/mainApi/index'
import rightBox from '~/components/right-box'
import Header from '~/components/index-header.vue'
import MyFooter from '~/components/Footer.vue'
export default {
    head() {
        return {
            title: "福居网首页"
        }
    },
  async asyncData () {
    let  bannerData  = await axios.get(api.paramToUrl(api.adLists,{type:0,position:0}));
    let advisData = await axios.get(api.paramToUrl(api.linkData,{type:3,position:0}));
    let newHouseData = await axios.get(api.paramToUrl(api.recommend,{type:0,position:0}));
    return {
        bannerData: bannerData.data.data,
        advisData:advisData.data.datas,
        newHouseData:newHouseData.data.new,
        secondUsedData:newHouseData.data.used,
        retalData:newHouseData.data.retal
    }
  },
    data(){
      return{
          swiperOption:{
              autoplay:true
          },
          selectIndex:0,
          placeholderText:"输入小区名查找二手房",
      }
    },
    components:{
        rightBox,
        Header,
        MyFooter
    },
    watch:{
        selectIndex(newValue,oldValue){
            switch (newValue){
                case 0:
                    this.placeholderText="输入小区名查找二手房";
                    break;
                case 1:
                    this.placeholderText="输入楼盘名进行搜索";
                    break;
                case 2:
                    this.placeholderText="输入小区名可以查找出租的房屋";
                    break;
                case 3:
                    this.placeholderText="输入小区名搜索学区房";
                    break;
                case 4:
                    this.placeholderText="找小区要输入小区名";
                    break;
            }
        }
    },
    directives:{
        banner:{
            inserted(el,binding,vnode){
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
                    setBannerHeight();
                    window.onresize = setBannerHeight;
                }
            },
        }
    },
}
</script>
<style>
    img.mypicture{
        display: block;
        width: 100%;
    }
</style>
<style scoped>

    img{
        border-style: none;
    }
    .wrap>.banner{
        position: relative;
    }
    .wrap>.content{
        width: 1100px;
        margin:0 auto;
    }
    .index-container{
        width: 1100px;
        margin:0 auto;
        position: absolute;
        bottom:125px;
        left:125px;
        z-index: 99;
    }
    .link-item{
        position: relative;
        padding:15px 10px;
        color:#fff;
        cursor: pointer;
        font-size: 16px;
    }
    .index-container .active::after{
        content: "";
        display: block;
        position: absolute;
        bottom:-10px;
        left:50%;
        transform: translateX(-50%);
        border: 10px solid transparent;
        border-bottom: 10px solid #fff;
    }
    .link-item:first-child{
        padding-left:0;
    }
    .index-container .active{
        font-weight: 700;
        cursor: pointer;
    }
    .search-button input.fll{
        outline: none;
        font-size: 16px;
        padding-left:10px;
    }
.search-button input{
    width: 700px;
    height: 60px;
    border: none;
    padding-left:5px;
    margin-top:10px;
    background-color: #fff;
}
    .search-btn{
        width: 150px;
        height: 60px;
        line-height: 60px;
        text-align: center;
        color:#fff;
        cursor: pointer;
        margin-top:10px;
        background-color:#c30d23;
    }
    .map-btn{
        position:absolute ;
        right: 50px;
        bottom: 0;
        z-index: 99;
        width:180px;
        height:60px;
        cursor: pointer;
        background-color: #5f1985;
        line-height: 60px;
        text-align: center;
        border-radius: 3px;
    }
    .map-btn a{
        color: #fff;
        font-size: 16px;
    }
    .map-btn a:hover{
        color:#fff;
    }
    .map-btn a img{
        vertical-align: middle;
        padding-right: 10px;
    }
    /*头部广告*/
    .wrap>.content .top-btngroup{
        width: 100%;
        margin: 40px 0;
        display: table;
    }
    .wrap>.content .top-btngroup .btn{
        display: table-cell;
        text-align: center;
        box-sizing: border-box;
        padding:0 40px;
        width: 25%;
        vertical-align: top;
    }
    .wrap>.content .top-btngroup .btn>a{
        display: inline-block;
        width: 100%;
    }
    .wrap>.content .top-btngroup .btn>a img{
        height:90px;
    }
    .wrap>.content .top-btngroup .btn>a .title{
        font-size: 20px;
        color:#333;
        margin-top: 20px;
        margin-bottom: 10px;
    }
    .wrap>.content .top-btngroup .btn>a .text{
        font-size: 14px;
        color:#666;
    }
    a,a:hover,a:visited{
        color:#000;
        text-decoration: none;
    }
    .lunbo{
        position: relative;
    }
    .lunbo .mask{
        position: absolute;
        z-index: 99;
        background-color: rgba(0,0,0,.3);
        width: 100%;
        height: 100%;
        top:0;
        left: 0;
    }
    /*特色*/
    .wrap>.content .feature{
        width: 100%;
        height: 228px;
        margin-bottom: 40px;
        margin-top:40px;
    }
    .wrap>.content .second{
        margin:40px 100px;
    }
    .wrap>.content .feature{
        display: inline-block;
        width: 300px;
        position: relative;
        float: left;
    }
    .wrap>.content .features .feature img{
        width: 100%;
    }
    .wrap>.content .features .feature .featureText{
        position: absolute;
        color:#fff;
        font-size: 24px;
        top:140px;
        width: 220px;
        left:50%;
        margin-left:-110px;
        text-align: center;
        letter-spacing: 2px;
    }
    /*精品新房*/
    .content .house-common{
        width: 100%;
        margin-bottom: 40px;
    }
    .content .house-common .top{
        margin-bottom:20px;
    }
    .content .house-common .top .title{
        font-size: 30px;
        font-weight: bolder;
        color:#333;
    }
    .content .house-common .top .more a{
        font-size: 16px;
        color:#999;
    }
    .content .house-common .house-tagLine{
        margin-bottom: 40px;
        color:#666;
    }
    .content .house-common .houses>:first-child.house{
        margin-left:0;
    }
    .content .house-common .houses .house{
        position: relative;
        margin-left: 37px;
        width: 342px;
    }
    .content .house-common .houses .house .house-img{
        width: 342px;
        height: 257px;
        overflow: hidden;
        position: relative;
    }
    .content .house-common .houses .house .house-img img{
        height:257px;
        width: 100%;
        transition: all 2s;
        position: absolute;
        top:0;
        left: 0;
    }
    .content .house-common .houses .house .house-img img:hover{
        transform: scale(1.1);
    }
    .content .house-common .houses .house .tags{
        position: absolute;
        top:0;
        left:0;
        z-index: 2;
        width: 100%;
        font-size: 14px;
        color:#fff;
    }
    .content .house-common .houses .house .bottom-content{
        position: absolute;
        left: 0;
        bottom:0;
        width: 100%;
        color:#fff;
        box-sizing: border-box;
        padding:5px 10px;
        font-size: 16px;
        background-color: rgba(0,0,0,.5);
    }
    /*二手优品*/
    .content .house-common .houses .house .price-tag{
        position: absolute;
        left:0;
        top:10px;
        z-index: 2;
        min-width: 70px;
        height: 50px;
        line-height: 50px;
        font-size: 20px;
        padding-left: 10px;
        padding-right: 20px;
        background: url(../assets/img/pricetag.png) no-repeat;
        background-size: 100% 100%;
        color:#fff;
    }
    .content .house-common .houses .house .bottom{
        height: 54px;
    }
    .content .house-common .houses .house .bottom .addr-name{
        font-size: 16px;
        color:#333;
        margin-top:20px;
        margin-bottom: 20px;
    }
    .content .house-common .houses .house .bottom .house-feature{
        width: 342px;
        font-size: 14px;
        color:#666;
    }
    .content .house-common .houses .house .bottom span{
        margin-right: 5px;
    }
    /*精品租房*/
    .content .house-common .houses .house .bottom span.price-prices{
        float: right;
        color: #cf0d23;
    }
    .house-img img{
        min-height: 257px;
    }
    .fleft{
        float: left;
    }
    .fright{
        float:right;
    }
</style>
