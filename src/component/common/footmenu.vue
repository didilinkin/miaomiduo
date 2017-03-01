<style>

/* line 1, ../sass/ie.scss */

#footMenu {
    width: 100%;
    height: 0.8rem;
    position: fixed;
    overflow: hidden;
    bottom: 0rem;
    padding: 0 0 0.1rem;
    z-index: 3;
}

#footMenu a {
    display: block;
    float: left;
    width: 1.5rem;
    background: #fff;
    height: 1.5rem;
    border-radius: 50%;
    border: 1px solid #a5d7ee;
    box-sizing:border-box;
}

#footMenu a i {
    text-align: center;
    font-size: 0.4rem;
    color: #a5d7ee;
    /*background: url('../../../src/assets/images/icn/home.png') no-repeat;
    background-size: 0.56rem 0.44rem;*/
}

#footMenu .mall i {
    position: relative;
    top: -0.06rem;
}

#footMenu a i{
    display: block;
    width: 0.56rem;
    height: 0.44rem;
    margin: 0.14rem auto 0;
}

#footMenu a p{
    color: #a5d7ee;
    font-size: 0.24rem;
    text-align: center;
}

#footMenu a p.cur{
    color: #fff;
}
#footMenu a i.cur{
    color: #fff;
}
#footMenu a.cur{
    background: #a5d7ee;
}

.foot-enter-active,
.foot-leave-active {
    transition: all 0.2s;
}

.foot-enter,
.foot-leave-active {
    margin-bottom: -0.89rem;
}

</style>

<template>
    <transition name="foot">
        <div id="footMenu" v-if="true">
            <router-link to="/index" class="index" :class="[iscur==1 ?'cur':'']" @click="heiline(1)">
                <i class="iconfont icon-cat" :class="[iscur==1 ?'cur':'']"></i>
                <p :class="[iscur==1 ?'cur':'']">喵zone</p>
            </router-link>
            <router-link to="/mall" class="mall" :class="[iscur==2 ?'cur':'']" @click="heiline(2)">
                <i class="iconfont icon-pussy" :class="[iscur==2 ?'cur':'']"></i>
                <p :class="[iscur==2 ?'cur':'']">喵商城</p>
            </router-link>
            <router-link to="/tcshop" class="tcshop" :class="[iscur==3 ?'cur':'']" @click="heiline(3)">
                <i class="iconfont icon-cat1" :class="[iscur==3 ?'cur':'']"></i>
                <p :class="[iscur==3 ?'cur':'']">喵服务</p>
            </router-link>
            <router-link to="/shopCart" class="shopcar" :class="[iscur==4 ?'cur':'']" @click="heiline(4)">
                <i class="iconfont icon-ziyuan" :class="[iscur==4 ?'cur':'']"></i>
                <p :class="[iscur==4 ?'cur':'']">购物车</p>
            </router-link>
            <router-link to="/user" class="user" :class="[iscur==5 ?'cur':'']" @click="heiline(5)">
                <i class="iconfont icon-mood" :class="[iscur==5 ?'cur':'']"></i>
                <p :class="[iscur==5 ?'cur':'']">铲屎官</p>
            </router-link>
        </div>
    </transition>
</template>

<script type="text/javascript">

export default {
    data() {
            return {
                iscur: null,
                show: true
            }
        },
        watch: {
            // 如果路由有变化，会再次执行该方法
            '$route': 'changeiscur'
        },
        methods: {
            heiline: function(num) {
                this.iscur = num;
            },
            changeiscur: function() {
                let path = this.$route.path;
                switch (path) {
                    case '/index':
                        this.iscur = 1
                        break;
                    case '/mall':
                        this.iscur = 2
                        break;
                    case '/tcshop':
                        this.iscur = 3
                        break;
                    case '/shopCart':
                        this.iscur = 4
                        break;
                    case '/user':
                        this.iscur = 5
                        break;
                    default:
                        break;
                }
            }
        }
}

</script>
