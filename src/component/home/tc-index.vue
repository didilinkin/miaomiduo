<style>
.tc-box header{

}
.tc-box header #areaName{
    color: #fff;
    float: left;
}
.tc-box header #areaName i{
    width: 0.4rem;
    color: #fff;
    float: right;
}
.tc-box header div{
    float: left;
}
.kyyq .iconfont {
    color: #ff7e42;
}
.searchBox{
    background: #fff;
    width: 4.8rem;
    margin-left: 0.15rem;
    border-radius: 0.08rem;
}
.tc-box .icon-kefu{
    color: #fff;
    float: right;
}

</style>

<template>
    <div class="tc-box">
        <header class="clearfix">
            <router-link to="/selectArea" id="areaName">{{positionData.city}}<i class="iconfont icon-down"></i></router-link>
            <!-- <div class="sc" @click="searchShow=true">优兑商城</div> -->
            <div class="searchBox" @click="searchShow=true">
                <i class="iconfont icon-iconfontsearch"></i>输入你想要搜索的商品
            </div>
            <a href="tel:4000801111" class="call"><i class="iconfont icon-kefu"></i></a>
        </header>
        <banner v-bind:banner="{styleObj:{},itemData:cateMenuData,dataType:3,filterType:5}" v-bind:bannerConfig="bannerConfig"></banner>
        <kyyq v-if="userInfo.isLogin" v-bind:yqData="userInfo.wallerData"></kyyq>
        <ztgg></ztgg>
        <tcHot></tcHot>
        <transition name="search-fade">
            <search v-show="searchShow" :searchType="'tc'" v-on:hide="hideSearch"></search>
        </transition>
    </div>
</template>

<script>

import {
    mapGetters
}
from 'vuex'
import banner       from      './../common/banner.vue'
import search       from      './../common/search.vue'
import kyyq         from      './kyyq.vue'
import ztgg         from      './../common/ztgg.vue'
import tcHot        from      './tc-hot.vue'

const components = {
    banner, search, kyyq, ztgg, tcHot
}

export default {
    data() {
        return {
            searchShow : false,
            bannerConfig : {
                direction: 'horizontal',
                slidesPerView: '4',
                slidesPerColumn: 2,
                slidesPerColumnFill: 'row',
                spaceBetween: 50,
                observer: true, //修改swiper自己或子元素时，自动初始化swiper
                observeParents: true,
                //修改swiper的父元素时，自动初始化swiper
                // 如果需要分页器
                pagination: '.swiper-pagination'
            }
        }
    },
    computed: mapGetters({
        filterState  : 'tcFilterState',
        cateMenuData : 'cateMenuData',
        positionData : 'positionData',
        userInfo     : 'userInfo'
    }),
    created() {
        this.$store.dispatch('getTcIndexData',{areaId:this.filterState.areaId});
    },
    methods : {
        hideSearch : function(){
            this.searchShow = false;
        }
    },
    name: 'tc-index',
    components: components
}

</script>
