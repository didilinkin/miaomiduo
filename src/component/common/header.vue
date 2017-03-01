<style>
/* line 6, ../sass/ie.scss */
header {
    height: 0.6rem;
    background: #a5d7ee;
    border-bottom: 0.01rem solid #dfdfdf;
    padding: 0.1rem 0.3rem;
    position: relative;
}
header .backBtn {
    position: absolute;
    color: #fff !important;
}
header .title{
    color: #fff;
}
header .subMenu{
    position: absolute;
    color: #fff !important;
}
header .areaName {
    color: #fff;
    position: absolute;
    left: 0.27rem;
    height: 0.54rem;
    line-height: 0.54rem;
    width: 1.5rem;
}
header .areaName a {
    color: #fff;
    font-size: 0.3rem;
    float: left;
}
header .areaName i {
    margin-left: 0.06rem;
    line-height: 0.54rem;
    position: relative;
    top: 0.03rem;
}
header p {
    font-size: 0.32rem;
    text-align: center;
    line-height: 0.6rem;
}
header .rightTxt {
    display: block;
    width: 1.3rem;
    height: 0.6rem;
    text-align: right;
    line-height: 0.6rem;
    position: absolute;
    z-index: 1;
    right: 0.2rem;
    top: 0.1rem;
    font-size: 0.3rem;
}
header .iconfont {
    font-size: 0.4rem;
}
header .sc {
    width: 73%;
    font-size: 0.3rem;
    text-indent: 1em;
    color: #aaa;
    background: #fff;
    position: absolute;
    left: 0.86rem;
    border-radius: 0.04rem;
}
header .rightIcon {
    color: #fff;
    text-align: center;
    position: absolute;
    z-index: 1;
    right: 0.15rem;
    top: 0.15rem;
}
</style>

<template>

<header class="nav-header">
    <!-- <router-link class="backBtn" to="/index"></router-link> -->
    <i v-if="headConfig.backBtn?headConfig.backBtn:false" @click="backfn()"        class="backBtn iconfont icon-zuo"></i>
    <i v-if="headConfig.subMenu?headConfig.subMenu:false" @click="emit('showSubMenu')" class="subMenu iconfont icon-liebiao"></i>
    <div class="areaName" v-show="headConfig.areaName?headConfig.areaName:false">
        <router-link to="/selectArea"  id="areaName">{{positionData.city}}</router-link>
        <i class="iconfont icon-down"></i>
    </div>
    <p v-if="headConfig.title?headConfig.title:false" class="title">{{headConfig.title}}</p>
    <div v-if="headConfig.sc?headConfig.sc:false" class="sc" @click="emit('showAddMood')">写点什么吧......</div>
    <i v-if="headConfig.rightIcon" class="rightIcon iconfont" :class="headConfig.rightIconClass" @click="emit('showSearch')"></i>
    <!-- <a class="rightTxt" v-if="rightIcon&&rightIcon.txt" @click="rIconEvent()">{{rightIcon.txt}}</a> -->
</header>

</template>

<script type="text/javascript">

import {
    mapGetters
}
from 'vuex'
export default {
    computed: mapGetters({
        positionData: 'positionData'
    }),
    data() {
        return {
            areaName : false,
            backBtn : true
        }
    },
    methods: {
        backfn: function() {
            this.$router.go(-1)
        },
        emit : function(str){
            this.$emit(str);
        }
    },
    props: ['headConfig','rightIcon'],
    created() {
        let path = this.$route.path;
        switch (path) {
            case '/tcshop':
                this.areaName = true;
                this.backBtn = false;
                break;
            default:
                break;
        }
    }
}

</script>
