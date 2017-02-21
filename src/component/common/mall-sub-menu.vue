<style>

.sub-menu {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 4;
    width: 100%;
    height: 100%;
}

.sub-menu-box{
    width: 55%;
    height: 100%;
    background: rgba(165,215,238,0.6);
}
.sub-menu-box .user-info{
    padding-top: 0.4rem;
    margin-bottom: 1rem;;
}
.sub-menu-box .user-info img{
    width: 60%;
    margin: 0 auto 0.1rem;;
    display: block;
    border-radius: 50%;
}
.sub-menu-box .user-info p{
    text-align: center;
    color: #fff;
    font-size: 0.36rem;
}
.sub-menu-list{
    margin: 0 10px;
}
.sub-menu-list li{
    text-align: center;
    border-bottom: 1px solid #fff;
    font-size: 0.36rem;
    line-height: 1rem;
}

</style>

<template>

<div class='sub-menu'>
    <div class="sub-menu-box" @click="hide">
        <div class="user-info">
            <img src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2790396100,129677017&fm=23&gp=0.jpg"/>
            <p>蕾姆</p>
        </div>
        <ul class="sub-menu-list">
            <li>猫罐头/妙鲜包</li>
            <li>猫猫零食</li>
            <li>猫猫医疗</li>
            <li>猫猫保健品</li>
            <li>猫猫香波</li>
            <li>日常用品</li>
            <li>猫猫玩具</li>
            <li>猫衣服/猫窝</li>
            <li>美容器材</li>
        </ul>
    </div>
</div>

</template>

<script type="text/javascript">

import {
    mapGetters
}
from 'vuex'
export default {
    computed: mapGetters({
        }),
    data() {
        return {
            }
    },
    methods:{
        hide : function(){
            this.$emit('hide')
        }
    },
    props: ['searchType'],
    created() {
    }
}

</script>
