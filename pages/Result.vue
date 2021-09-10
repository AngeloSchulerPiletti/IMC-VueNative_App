<template>
  <view class="container flex_center">
      <view class="top">
          <image v-if="!icon" class="img" :source="require('../assets/warning.png')"/>
          <image v-else class="img" :source="require('../assets/checked.png')"/> 
      <text class="txt_h3">Sua situação é de:</text>
    <text class="txt_h1"> {{ situation }}</text>
      </view>
      <view class="bottom flex_center">
          <text class="txt_h3">Seus dados:</text>
          <view class="data_container flex_center">
              <text class="txt_h2">{{height}}m</text>
              <text class="txt_h2">{{weight}}Kg</text>
          </view>
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
  mounted(){
      var result = this.navigation.getParam('userData');
      this.situation = result[0];
      this.weight = (result[1][0]).toFixed(2);
      this.height = ((result[1][1])/100).toFixed(2);
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
/* ============= PRESETS ============ */

.container{
    width: 100%;
    height: 100%;
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
    
}
.data_container{
    flex-direction: row;
}
</style>
