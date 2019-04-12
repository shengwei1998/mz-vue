<template>
<div class="swiper-container">
    <div class="swiper-wrapper">
        <div class="swiper-slide"
            v-for="(item,index) in banImg"
            :key="index"
        >
            <img :src="item.imgUrl" alt="">
        </div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>
</div>
</template>

<script>
import Swiper from 'swiper'
import '../../node_modules/swiper/dist/css/swiper.min.css'
export default {
  props: {
    banImg: {
      type: Array
    }
  },
  methods: {
    bannerScroll () {
      if (!this.swiper) {
        this.swiper = new Swiper('.swiper-container', {
          loop: true,
          autoplay: {
            delay: 1000,
            disableOnInteraction: false
          },
          pagination: {
            el: '.swiper-pagination'
          }
        })
      }
    }
  },

  updated () {
    this.bannerScroll()
  }
}
</script>

<style scoped>
  .swiper-container {
      width: 100%;
      height: 200px;
  }
  .swiper-container img {
      width: 100%;
      height: 200px;
  }
  .swiper-pagination-bullet{
      background: #fff;
      opacity: 1;
  }
  .swiper-pagination-bullet-active{
      background: orange;
  }
</style>
