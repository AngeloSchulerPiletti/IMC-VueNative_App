<template>
    <view class="container">
        <view class="top">
            <image class="img" :source="require('../assets/muscle.png')" />
        </view>
        <view class="bottom">
            <inputs @success="goResult"/>
        </view>
    </view>
</template>

<script>
import Inputs from "../components/Inputs";

export default {
    props:{
        navigation:{
            type: Object,
        }
    },
    methods:{
        goResult(param){
            this.navigation.navigate("Result", {userData: param});
        }
    },
    components:{
        Inputs,
    }
}
</script>

<style>
.container{
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
.top{
    width: 150;
    height: 150;
    margin-bottom: 50;
}
.img{
    width: 100%;
    height: 100%;
}
.bottom{
    width: 100%;
    display: flex;
    align-items: center;
}

</style>