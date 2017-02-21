<style>
.kyyq {
    padding: 0 0.18rem;
    background: #fff;
    border-top: 1px solid #eee;
    height: 1rem;
    line-height: 1rem;
}

.kyyq .fl {
    font-size: 0.3rem;
}

.kyyq .fr {
    font-size: 0.25rem;
    color: #ff7e42;
}

.kyyq .fl b {
    color: #ff7e42;
}


</style>

<template>

<div class="kyyq clearfix">
    <div class="fl">
        <span>可使用优券：</span>
        <b>{{myWallerData.vouchers}}</b>
    </div>
    <router-link to="/index"  class="fr">
        <span>我要使用</span>
        <i class="iconfont icon-right"></i>
    </router-link>
</div>

</template>

<script type="text/javascript">
import {
    mapGetters
}
from 'vuex'

export default {
    data() {
        return {}
    },
    computed: mapGetters({
        myWallerData: 'myWallerData'
    }),
    methods: {},
    created() {
        this.$store.dispatch('getWallerData')
    },
    props: ['yqData']
}

</script>
