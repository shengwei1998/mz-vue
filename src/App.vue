<template>
  <div id="app">
    <router-view></router-view>
    <NavBar :tabs="tabs"></NavBar>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'

export default {
  name: 'app',

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

<style>
  @import './styles/base.css';
</style>
