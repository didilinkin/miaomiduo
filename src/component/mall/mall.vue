<style>



</style>

<template>

<div>
    <headnav v-bind:headConfig="headConfig" v-on:showSubMenu="showSubMenu"></headnav>
    <transition name="subMenu-fade">
        <subMenu v-show="subMenu" v-on:hide="hideSubMenu"></subMenu>
    </transition>
</div>

</template>

<script type="text/javascript">

import {
    mapGetters
}
from 'vuex'
import headnav from './../common/header.vue'
import subMenu  from './../common/mall-sub-menu.vue'
const components = {
    headnav, subMenu
}
export default {
    data() {
        return {
            headConfig : {
                title : "喵商城",
                subMenu : true
            },
            subMenu : false
        }
    },
    computed: mapGetters({
        navMenuData: 'getNavMenu',
        subClassData: 'getSubClass'
    }),
    components: components,
    methods: {
        showNum: function() {
            alert(1)
        },
        showSubMenu : function(){
            this.subMenu = true;
        },
        hideSubMenu : function(){
            this.subMenu = false;
        }
    },
    created() {
        this.$store.dispatch('getNavMenu', {
            areaId: -1
        });
    }
}

</script>
