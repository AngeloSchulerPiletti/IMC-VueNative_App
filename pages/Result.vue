<template>
  <view class="container flex_center">
    <view class="top flex_center">
      <image
        v-if="!icon"
        class="img"
        :source="require('../assets/warning.png')"
      />
      <image v-else class="img" :source="require('../assets/checked.png')" />
      <text class="txt_h3">Sua situação é de:</text>
      <text class="txt_h1 txt_prime"> {{ situation }}</text>
    </view>
    <view class="center flex_center">
      <text class="txt_h3">Seus dados:</text>
      <view class="data_container flex_center">
        <text class="txt_h2 txt_data">{{ height }}m</text>
        <text class="txt_h2 txt_data">{{ weight }}Kg</text>
      </view>
    </view>
    <view class="bottom flex_center">
        <touchable-opacity class="button" :on-press="goCalculate">
            <text class="txt_btn">Novo Cáclculo</text>
        </touchable-opacity>
        <touchable-opacity class="button covered" :on-press="goWelcome">
            <text class="txt_btn txt_btn2">Sair</text>
        </touchable-opacity>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      situation: "",
      height: "",
      weight: "",
      icon: false,
    };
  },
  props: {
    navigation: {
      type: Object,
    },
  },
  mounted() {
    var result = this.navigation.getParam("userData");
    this.situation = result[0];
    this.weight = result[1][0].toFixed(2);
    this.height = (result[1][1] / 100).toFixed(2);
    this.icon = result[2];
  },
  methods: {
    goCalculate() {
      this.navigation.navigate("Calculate");
    },
    goWelcome() {
      this.navigation.navigate("Welcome");
    },
  },
};
</script>

<style>
/* ============= PRESETS ============ */
.flex_center {
  display: flex;
  align-items: center;
}

.txt_h1 {
  color: #1d4859;
  font-size: 30;
  text-transform: uppercase;
  font-weight: bold;
}
.txt_h2 {
  color: #1d4859;
  font-size: 24;
  text-transform: uppercase;
  font-weight: bold;
}
.txt_h3{
    font-size: 16;
}
/* ============= PRESETS ============ */

.container {
  width: 100%;
  height: 100%;
  justify-content: center;
}
.top {
  width: 100%;
justify-content: center;
    margin-bottom: 80;
}
.img {
  width: 150;
  height: 150;
    margin-bottom: 20;
}
.txt_prime{
    width: 80%;
    text-align: center;
}
.center {
}
.data_container {
  flex-direction: row;
  justify-content: space-around;
}
.txt_data{
    width: 45%;
    text-align: center;
}
.bottom{
    flex-direction: row;
    margin-top: 20;
    justify-content: space-around;
    width: 100%;
}
.button{
    border-color: #1d4859;
    border-width: 2;
    border-radius: 10000;
  padding-top: 10;
  padding-bottom: 10;
  padding-left: 30;
  padding-right: 30;
}
.covered{
    background-color: #1d4859;
}
.txt_btn{
    font-size: 15;
    color: #1d4859;
}
.txt_btn2{
    color: #FAFAFA;
}
</style>
