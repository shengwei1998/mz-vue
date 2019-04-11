<template>
    <div>
        <ul class="nowWrap">
            <li class="now_li"
                v-for="item in mainList"
                :key="item.filmId"
            >
                <router-link :to="{ name: 'detail', params: { id: item.filmId }}">
                    <div class="now_li_img">
                        <img :src="item.poster" alt="">
                    </div>
                    <div class="now_li_mian">
                        <div class="now_li_mian01">
                            <span class="now_name">{{ item.name }}</span>
                            <span class="now_item">{{ item.filmType.name }}</span>
                        </div>
                        <div class="now_li_mian02">
                            <span class="label">观众评分 </span>
                            <span class="grade"> {{ item.grade }}</span>
                        </div>
                        <div class="now_li_mian03">
                            <span class="label">主演：{{ actorsFn(item.actors) }} </span>
                        </div>
                        <div class="now_li_mian04">
                            <span>{{ item.nation }} | {{ item.runtime }}分钟</span>
                        </div>
                    </div>
                    <div class="now_li_right">购票</div>
                </router-link>
            </li>
        </ul>

        <div class="now_loading" @click="loadMore" v-if="pageNum < totalPage">点击加载更多...</div>
        <div class="now_loading" v-else>别点了，没有了</div>
    </div>
</template>

<script>
/* ?cityId=440300&pageNum=1&pageSize=10&type=1&k=1539520 */
import Axios from 'axios';
export default {
    data() {
        return {
            mainList: [],
            pageNum: 1,
            pageSize: 10,
            total: 10,
        }
    },

    computed: {
        //总的页数
        totalPage() {
            return Math.ceil(this.total / this.pageSize);
        }
    },

    methods: {
        getList() {
            Axios.get("https://m.maizuo.com/gateway", {
                params: {
                    cityId: 440300,
                    pageNum: this.pageNum,
                    pageSize: this.pageSize,
                    type: 1,
                    k: 1539520
                },
                headers: {
                    'X-Client-Info': '{"a":"3000","ch":"1002","v":"1.0.0","e":"15546154461945620186257"}',
                    'X-Host':' mall.film-ticket.film.list'
                }
            }).then(res => {
                let data = res.data;
                if(data.status === 0){
                    this.total = data.data.total;
                    //this.mainList = data.data.films;
                    //追加
                    this.mainList = this.mainList.concat(data.data.films);
                }else{
                    alert(data.msg);
                }
            })
        },

        actorsFn(actors = []) {
            let temp = actors.map(item => {
                return item.name;
            })
            return temp.join('/');
        },

        loadMore() {
            this.pageNum++;
            this.getList();
        }
    },

    created() {
        this.getList()
    }
}

</script>

<style>
    .nowWrap{
        margin-left: 15px;
    }
    .nowWrap .now_li{
        padding: 15px 15px 15px 0;
        height: 94px;
        position: relative;
        border-bottom: 1px solid #ededed;
    }
    .now_li_img{
        width: 66px;
        height: 94px;
        background: rgb(249, 249, 249);
        float: left;
    }
    .now_li_img>img{
        width: 66px;
        height: 94px;
    }
    .now_li_mian{
        float: left;
        padding: 10px;
        width: calc(100% - 116px);
    }
    .now_li_mian .now_li_mian01{
        width: 100%;
    }
    .now_li_mian .now_li_mian01 .now_name{
        color: #191a1b;
        font-size: 16px;
        height: 22px;
        line-height: 22px;
        margin-right: 5px;
        display: inline-block;
        vertical-align: middle;
    }
    .now_li_mian .now_li_mian01 .now_item{
        font-size: 9px;
        color: #fff;
        background-color: #d2d6dc;
        height: 14px;
        line-height: 14px;
        padding: 0 2px;
        border-radius: 2px;
        display: inline-block;
        vertical-align: middle;
    }
    .now_li_mian .now_li_mian02{
        width: 100%;
    }
    .now_li_mian .label{
        font-size: 13px;
        margin-top: 4px;
        color: #797d82;
    }
    .now_li_mian .now_li_mian02 .grade{
        color: #ffb232;
        font-size: 14px;
    }
    .now_li_mian .now_li_mian03{
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        width: 100%;
    }
    .now_li_right{
        line-height: 25px;
        height: 25px;
        width: 50px;
        color: #ff5f16;
        font-size: 13px;
        text-align: center;
        border-radius: 2px;
        position: relative;
        float: right;
        border: 1px solid #ff5f16;
        top: -65px;
        right: 0;
        bottom: 0;
        left: 0;
        border-radius: 4px;
    }
    .now_loading{
        text-align: center;
        height: 36px;
        line-height: 36px;
    }
</style>