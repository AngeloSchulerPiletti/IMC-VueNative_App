<template>
  <view class="container">
    <view class="top">
      <text-input class="input_field" v-model="weight" placeholder="Qual o seu peso?"/>
      <text-input class="input_field" v-model="height" placeholder="Qual a sua altura?"/>
    </view>
    <view class="bottom">
      <touchable-opacity class="button" :on-press="calculate">
        <text class="txt">Calcular</text>
      </touchable-opacity>
    </view>
  </view>
</template>

<script>
export default {
  data(){
    return{
      weight: "",
      height: "",
    }
  },
  methods: {
    calculate(){
      var weight = Number(this.weight),
          height = Number(this.height);

      
      this.$emit('success', 'teste');
    },
  },
}
</script>

<style scoped>
.container{
  align-items: center;
  justify-content: center;
  width: 100%;
  display: flex;
}
.top{
  width: 100%;
  display: flex;
  align-items: center;
}
.input_field{
  border-color: #1D4859;
  border-width: 1;
  width: 80%;
  height: 50;
  text-align: center;
  font-size: 14;
  border-radius: 5;
  margin-bottom: 15;
}
.bottom{
  margin-top: 30;
  width: 100%;
  display: flex;
  align-items: center;
  color: aqua;
}
.button{
  background-color: #1D4859;
  padding-top: 10;
  padding-bottom: 10;
  padding-left: 30;
  padding-right: 30;
  border-radius: 1000;
  /* background-color: red; */
}
.txt{
  color: #FAFAFA;
  font-size: 15;
}
</style>