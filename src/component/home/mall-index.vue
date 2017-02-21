<style>

#app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}

.index-box header {
    width: 6.9rem;
    background: #a5d7ee;
    color: #fff;
    line-height: 0.6rem;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 2;
}
.index-box header .icon-liebiao{
    color: #fff;
    position: absolute;
}
.index-box header a {
    font-size: 0.27rem;
}

.index-box .sc {
    width: 73%;
    font-size: 0.3rem;
    text-indent: 1em;
    color: #aaa;
    background: #fff;
    position: absolute;
    left: 0.86rem;
    border-radius: 0.04rem;
}

.app-fade-enter-active {
    transition: all .3s ease;
}

.app-fade-leave-active {
    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}

.app-fade-enter,
.app-fade-leave-active {
    padding-right: 500px;
    padding-left: 500px;
    opacity: 0;
}
.search-fade-enter-active {
  transition: all .3s ease;
}
.search-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.search-fade-enter, .search-fade-leave-active {
  transform: translateX(-10px);
  opacity: 0;
}
.subMenu-fade-enter-active {
  transition: all .6s ease;
}
.subMenu-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.subMenu-fade-enter, .subMenu-fade-leave-active {
  transform: translateX(-10px);
  opacity: 0;
}
</style>

<template>
<div class="index-box">
    <headnav v-on:showAddMood="addMood=true" v-on:showSubMenu="subMenu=true" v-bind:headConfig="headConfig"></headnav>
    <banner v-bind:banner="{styleObj:{height:'3rem'},itemData:getCarousel,dataType:1,filterType:5}" :bannerConfig="bannerConfig"></banner>
    <transition name="subMenu-fade">
        <subMenu v-show="subMenu" v-on:hide="hideSubMenu"></subMenu>
    </transition>
    <transition name="search-fade">
        <addMood v-show="addMood" v-on:hide="hideAddMood"></addMood>
    </transition>
</div>
</template>

<script>

import {
    mapGetters
}
from 'vuex'
import headnav  from './../common/header.vue'
import banner   from './../common/banner.vue'
import subMenu  from './../common/zone-sub-menu.vue'
import addMood  from './../common/add-mood.vue'

const components = {
    headnav, banner, subMenu, addMood
}

export default {
    data() {
        return {
            headConfig : {
                subMenu : true,
                sc : true
            },
            subMenu    : false,
            addMood    : false,
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
        getCarousel: 'getCarousel',
        getChannelInfo:'getChannelInfo'
    }),
    created() {
        this.$store.dispatch('getmallIndexData',{type:1});
    },
    methods : {
        hideSubMenu : function(){
            this.subMenu = false;
        },
        hideAddMood : function(){
            this.addMood  = false;
        }
    },
    name: 'mood-index',
    components: components
}

</script>
