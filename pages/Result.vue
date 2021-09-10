<template>
  <view>
    <text>O param é: {{ situation }}</text>
  </view>
</template>

<script>
export default {
  data() {
    return {
      situation: "",
      height: "",
      weight: "",
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
      this.weight = result[1][0];
      this.height = result[1][1];
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

<style></style>
