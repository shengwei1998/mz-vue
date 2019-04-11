<template>
    <div>
        <router-view></router-view>
        <NavBar :tabs="tabs"></NavBar>
    </div>
</template>

<script>
import NavBar from '../components/NavBar.vue'

export default {
    data: function(){
    return {
        tabs: [
            { name: '电影', path: '/films', icon: 'icon-dianying'},
            { name: '影院', path: '/cinemas', icon: 'icon-huaban'},
            { name: '特惠', path: '/asd', icon: 'icon-tehui'},
            { name: '我的', path: '/center', icon: 'icon-weibiaoti-'},
        ]
        }
    },
    components: {
        NavBar,
    }
}
</script>
