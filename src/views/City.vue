<template>
    <div id="home">
        <div class="city_header">
            <div class="c_left"><i class="iconfont icon-X"></i></div>
            <div class="c_right">当前城市</div>
        </div>
        <div class="city_search">
            <div class="sea_outer">
                <i class="iconfont icon-sousuo"></i>
                <input type="text" placeholder="请输入城市名或拼音" class="city_txt">
            </div>
        </div>
        <div class="city_main">
            <div class="main_top">GPS定位你所在城市</div>
            <div class="mian_bottom">定位失败</div>
            <div class="main_hot">热门城市</div>
            <ul class="main_cen">
                <li><a href="#">北京</a></li>
                <li><a href="#">上海</a></li>
                <li><a href="#">广州</a></li>
                <li><a href="#">深圳</a></li>
            </ul>
        </div>
        <ul class="main">
            <li>
                <p>A</p>
                <ul class="two_main">
                    <li><a href="#">按样</a></li>
                    <li><a href="#">按样</a></li>
                    <li><a href="#">按样</a></li>
                    <li><a href="#">按样</a></li>
                    <li><a href="#">按样</a></li>
                    <li><a href="#">按样</a></li>
                </ul>
            </li>
        </ul>
        <div class="city_nav">
            <ul>
                <li>A</li>
                <li>B</li>
                <li>C</li>
                <li>D</li>
                <li>E</li>
                <li>F</li>
                <li>G</li>
                <li>H</li>
                <li>I</li>
                <li>J</li>
                <li>K</li>
                <li>L</li>
                <li>M</li>
                <li>N</li>
                <li>O</li>
                <li>P</li>
                <li>Q</li>
                <li>R</li>
                <li>S</li>
                <li>T</li>
                <li>W</li>
                <li>X</li>
                <li>Y</li>
                <li>Z</li>
            </ul>
        </div>
    </div>
</template>

<style>
    body{
        overflow-x: hidden;
        background-color: #f4f4f4;
    }
    .city_header{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 44px;
        overflow: hidden;
        margin: 0;
        padding: 0;
        z-index: 300;
        background-color: #fff;
    }
    .c_left{
        width: 14%;
        float: left;
        height: 44px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .c_right{
        width: 72%;
        text-align: center;
        font-size: 17px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #191a1b;
        height: 44px;
    }
    .city_search{
        z-index: 2000;
        height: 30px;
        width: 100vw;
        background-color: #f4f4f4;
        position: fixed;
        padding: 10px 0;
        top: 44px;
    }
    .city_search .sea_outer{
        background-color: #fff;
        position: relative;
        border-radius: 3px;
        width: 90%;
        height: 30px;
        margin: auto;
    }
    .city_search .sea_outer>i{
        position: absolute;
        left: 7px;
        top: 0;
        line-height: 30px;
        font-size: 21px;
        color: #797d82;
        font-size: 20px;
    }
    .city_search .sea_outer>.city_txt{
        position: absolute;
        left: 33.5px;
        top: 0;
        height: 30px;
        width: calc(100% - 65px);
        border: 0;
    }
   .city_main{
        position: relative;
        overflow: hidden;
        padding-top: 94px;
        background: #fff;
        background-color: #fff;
        padding-left: 15px;
    }
    .city_main .main_top{
        font-size: 13px;
        color: #797d82;
        margin-bottom: 10px;
        padding-top: 15px;
    }
    .city_main .mian_bottom{
        width: calc((100vw - 33px)/3);
        text-align: center;
        height: 30px;
        background-color: #f4f4f4;
        line-height: 30px;
        border-radius: 3px;
        box-sizing: border-box;
        margin: 0 7.5px;
        font-size: 14px;
        color: #191a1b;
    }
    .city_main .main_hot{
        font-size: 13px;
        color: #797d82;
        margin: 10px 0;
    }
    .city_main .main_cen{
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        background: #fff;
        overflow-x: hidden;
    }
    .city_main .main_cen>li{
        width: calc((100vw - 78px)/3);
        text-align: center;
        
        margin: 8px;
        box-sizing: border-box;
        float: left;
        background-color: #f4f4f4;
        line-height: 30px;
        border-radius: 3px;
    } 
    .main>li>p{
        background-color: #f4f4f4;
        color: #797d82;
        margin: 0 0 0 15px;
        height: 30px;
        line-height: 30px;
        font-size: 12px;
    }
    .main .two_main{
        display: flex;
        background: #fff;
        justify-content: flex-start;
        align-content: center;
        flex-wrap: wrap;
        padding: 0 0 0 15px;
    }
    .main .two_main>li{
        height: 48px;
        width: calc((100vw - 33px)/3);
        text-align: center;
        float: left;
        line-height: 48px;
        border-bottom: 1px solid #ededed;
    }
    .city_nav{
        border: 0;
        position: fixed;
        top: 0;
        right: 0;
        z-index: 1999;
        width: 17px;
        height: 100%;
        padding-top: 165px;
        background-color: #fff;
    }
    .city_nav>ul>li{
        font-size: 12px;
        text-align: center;
    }
</style>