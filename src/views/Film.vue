<template>
    <div>
        <banner :banImg="bannerList"></banner>
    </div>
</template>

<script>
import axios from 'axios'
import banner from '../components/banner'
export default {
    data(){
        return {
            bannerList: []
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
        }
    },
    created(){
        this.getBanner();
    }
}
</script>