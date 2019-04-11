<template>
    <div class="filmBox">
        <banner :banImg="bannerList"></banner>
        
        <div class="film-wrap" :class="{'film-wrap-fixed': isFixedTabs}">
            <ul class="film_outer">
                <li v-for="item in filmType"
                    :key= "item.id"
                    :class="{ FilActive: cur === item.id}"
                    @click="change(item)"
                    >正在热映</li>
            </ul>
            <div class="miracle" :style="tabInkBarStyle">
                <span></span>
            </div>
        </div>
        <router-view></router-view>
    </div>
</template>

<script>
import axios from 'axios'
import banner from '../components/banner'
export default {
    data(){
        return {
            isFixedTabs: false,
            bannerList: [],
            filmType: [
                { id: 'nowPlaying', name: '正在热映', href: '/films/nowPlaying'},
                { id: 'comingSoon', name: '即将上映', href: '/films/comingSoon'},
            ],
            cur: this.$route.path.substr(7)
        }
    },
    computed: {
        tabInkBarStyle () {
            let obj = {
                transform: 'translate3d(0%, 0px, 0px)'
            }
            if (this.cur === 'comingSoon') {
                obj.transform = 'translate3d(100%, 0px, 0px)'
            }
            return obj;
        }
    },
    components: {
        banner,
    },
    methods: {
        getBanner(){
            axios.get('https://m.maizuo.com/gateway?type=2&cityId=440300&k=5067437',{
                headers: {
                    'X-Client-Info': '{"a":"3000","ch":"1002","v":"1.0.0","e":"15546154461945620186257"}',
                    'X-Host': 'mall.cfg.common-banner'
                }
            }).then(res => {
                let data = res.data;
                if(data.status === 0){
                    this.bannerList = data.data;
                } else{
                    alert(data.msg);
                }
            })
        },
        change(item) {
            this.cur = item.id;
            this.$router.push(item.href);
        },
        onScoll() {
            //计算滚动条距离顶部的距离
            let _this = this;
            let scrollTop = document.documentElement.scrollTop;
            /* if(scrollTop >= 210){
                _this.isFixedTabs = true;
            }else{
                _this.isFixedTabs = false;
            } */
        }
    },

    created(){
        this.getBanner();
    },

    activated() {
        window.addEventListener('scroll',this.onScoll);
    },
    
    deactivated() {
        window.removeEventListener('scroll',this.onScoll);
    }
}
</script>

<style>
    .filmBox{
        padding-bottom: 60px;
    }
    .film-wrap{
        width: 100%;
        height: 50px;
        border-bottom: 1px solid #ededed;
        position: sticky;
        top: 0;
        z-index: 99;
        background: #fff;
    }
    .film-wrap-fixed{
        position: fixed;
        background: #fff;
        z-index: 99;
        top: 0;
    }
    .film_outer{
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        line-height: 48px;
        height: 50px;
        position: relative;
         background: #fff;
    }
    .film_outer>li{
        width: 50%;
        height: 48px;
        font-size: 14px;
         background: #fff;
    }
    .film_outer>.FilActive{
        color: #ff5f16;
    }
    .film-wrap .miracle{
        width: 50%;
        transition: transform .6s; 
    }
    .miracle>span{
        border-bottom: 2px solid #ff5f16;
        border-radius: 20px;
        display: block;
        margin: auto;
        width: 56px;
    }
</style>