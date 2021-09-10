<template>
  <view class="container">
    <view class="top">
      <image class="img" :source="require('../assets/muscle.png')" />
    </view>
    <view class="bottom">
      <text class="txt_p">Calculadora de IMC</text>
      <touchable-opacity class="button" :on-press="goCalculate">
        <text class="txt">Próximo</text>
      </touchable-opacity>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    navigation: {
      type: Object,
    },
  },
  methods: {
    goCalculate() {
      this.navigation.navigate("Calculate");
    },
  },
};
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
.button{
  background-color: #1D4859;
  padding-top: 10;
  padding-bottom: 10;
  padding-left: 30;
  padding-right: 30;
  border-radius: 1000;
  margin-top: 10;
}
.txt{
  color: #FAFAFA;
  font-size: 16;
  text-align: center;
}
.txt_p{
    font-size: 20;
    margin-bottom: 5;
}
</style>
