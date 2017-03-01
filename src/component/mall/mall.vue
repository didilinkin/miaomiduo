<style>

</style>

<template>

<div>
    <headnav v-bind:headConfig="headConfig" v-on:showSubMenu="subMenu = true" v-on:showSearch="searchActive = true"></headnav>
    <banner v-bind:banner="{styleObj:{height:'3rem'},itemData:getCarousel,dataType:1,filterType:5}" :bannerConfig="bannerConfig"></banner>
    123123
    <transition name="subMenu-fade">
        <subMenu v-show="subMenu" v-on:hide="subMenu = false"></subMenu>
    </transition>
    <transition name="search-fade">
        <search v-bind:searchType="'mall'" v-show="searchActive" v-on:hide="searchActive = false"></search>
    </transition>
</div>

</template>

<script type="text/javascript">

import {
    mapGetters
}
from 'vuex'
import headnav  from './../common/header.vue'
import banner   from './../common/banner.vue'
import subMenu  from './../common/mall-sub-menu.vue'
import search   from './../common/search.vue'
const components = {
    headnav, banner, subMenu, search
}
export default {
    data() {
        return {
            headConfig : {
                title : "喵商城",
                subMenu : true,
                rightIcon : true,
                rightIconClass : 'icon-search'

            },
            subMenu : false,
            searchActive : false,
            bannerConfig : {
                direction: 'horizontal',
                autoplay: 2000,
                spend: 2000,
                loop: true,
                observer: true, //修改swiper自己或子元素时，自动初始化swiper
                observeParents: true,
                //修改swiper的父元素时，自动初始化swiper
                // 如果需要分页器
                pagination: '.swiper-pagination'
            }
        }
    },
    computed: mapGetters({
        navMenuData: 'getNavMenu',
        subClassData: 'getSubClass',
        getCarousel: 'getCarousel'
    }),
    components: components,
    methods: {
        showNum: function() {
            alert(1)
        }
    },
    created() {
        this.$store.dispatch('getNavMenu', {
            areaId: -1
        });
    }
}

</script>
