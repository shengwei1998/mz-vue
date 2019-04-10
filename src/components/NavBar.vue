<template>
    <ul>
        <li v-for="(item,index) in tabs"
            :key="index"
        >
            <router-link :to="item.path">
                <i :class="['iconfont',item.icon]"></i>
                {{ item.name }}
            </router-link>
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        tabs: {
            type: Array
        }
    }
}
</script>

<style>
    ul{
        position: fixed;
        bottom: 0;
        left: 0;
        height: 60px;
        width: 100%;
        display: flex;
        justify-content: space-around;
        align-items: center;
    }
    ul li{
        border-top: 1px #ccc solid;
        width: 25%;
        height: 60px;
        display: flex;
        justify-content: space-around;
        align-items: center;
    }
    ul li a{
        text-decoration: none;
        font-size: 14px;
        display: flex;
        flex-direction: column;
        align-items: center;
        color: #000;
    }
    ul li a i {
        font-size: 20px !important; 
    }
    .active{
        color: orange;
        background: #fff;
    }
</style>
