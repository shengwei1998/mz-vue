<template>
    <ul class="navbar-wrap">
        <li v-for="(item,index) in tabs"
            :key="index"
        >
            <router-link :to="item.path" active-class="active">
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

<style scoped>
    .navbar-wrap{
        position: fixed;
        bottom: 0;
        left: 0;
        height: 60px;
        width: 100%;
        display: flex;
        justify-content: space-around;
        align-items: center;
        background: #fff;
    }
    .navbar-wrap>li{
        border-top: 1px #ccc solid;
        width: 25%;
        height: 60px;
        display: flex;
        justify-content: space-around;
        align-items: center;
    }
    .navbar-wrap>li>a{
        text-decoration: none;
        font-size: 14px;
        display: flex;
        flex-direction: column;
        align-items: center;
        color: #000;
    }
    .navbar-wrap>li>a>i {
        font-size: 20px !important; 
    }
    .navbar-wrap>li>.active{
        color: orange;
        background: #fff;
    }
</style>
