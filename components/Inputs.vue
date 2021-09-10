<template>
  <view class="container flex_center">
    <view class="top flex_center">
      <view class="input_container flex_center">
        <text class="legend">Peso em Kg</text>
        <text-input
          keyboardType="numeric"
          class="input_field"
          v-model="weight"
          placeholder="Qual o seu peso?"
        />
      </view>
      <view class="input_container flex_center">
        <text class="legend">Altura em Centímetros</text>
        <text-input
          
          keyboardType="numeric"
          class="input_field"
          v-model="height"
          placeholder="Qual a sua altura?"
        />
      </view>
    </view>
    <view class="bottom flex_center">
      <touchable-opacity class="button" :on-press="calculate">
        <text class="txt">Calcular</text>
      </touchable-opacity>
    </view>
  </view>
</template>

<script>
import { Alert } from "react-native";
export default {
  data() {
    return {
      weight: "",
      height: "",
    };
  },
  watch: {
    height: function(){
      this.checkingField('height');
    },
    weight: function(){
      this.checkingField('weight');
    }
  },
  methods: {
    checkingField(field){
      if(this[field].length > 3){
        var heightArr = this[field].split('');
        this[field] = heightArr.splice(0, 3).join('');
      }
    },
    calculate() {
      if (!isNaN(this.weight) && !isNaN(this.height)) {
        var weight = Number(this.weight),
          height = Number(this.height);

        if (height < 50 || height > 250) {
          Alert.alert(
            "Altura inválida",
            "Por favor, adicione uma altura válida..."
          );
          //MUST SHOW AN ERROR
          return;
        }
        if (weight < 10 || weight > 200) {
          Alert.alert(
            "Peso inválido",
            "Por favor, adicione uma peso válido..."
          );
          //MUST SHOW AN ERROR
          return;
        }

        var calc = weight / (height / 100) ** 2;
        var message;

        if (calc < 13) {
          message = "Desnutrição";
        } else if (calc < 18.5) {
          message = "Pré-Desnutrição";
        } else if (calc < 25) {
          message = "Saudável";
        } else if (calc < 30) {
          message = "Pré-Obesidade";
        } else {
          message = "Obesidade";
        }

        this.$emit("success", [message, [weight, height]]);
      } else {
        Alert.alert("Dado inválido", "Por favor, adicione apenas números...");
      }
    },
  },
};
</script>

<style scoped>
/* ============= PRESETS ============ */
.flex_center {
  display: flex;
  align-items: center;
}
/* ============= PRESETS ============ */

.container {
  justify-content: center;
  width: 100%;
}
.top {
  width: 100%;
}
.input_container {
  width: 100%;
}
.legend {
  margin-bottom: 2;
}
.input_field {
  border-color: #1d4859;
  border-width: 1;
  width: 80%;
  height: 50;
  text-align: center;
  font-size: 14;
  border-radius: 5;
  margin-bottom: 15;
}
.bottom {
  margin-top: 30;
  width: 100%;
  color: aqua;
}
.button {
  background-color: #1d4859;
  padding-top: 10;
  padding-bottom: 10;
  padding-left: 30;
  padding-right: 30;
  border-radius: 1000;
  /* background-color: red; */
}
.txt {
  color: #fafafa;
  font-size: 15;
}
</style>
