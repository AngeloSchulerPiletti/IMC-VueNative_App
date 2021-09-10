<template>
  <view>
    <text>O param é: {{ result }}</text>
  </view>
</template>

<script>
export default {
  data() {
    return {
      result: "",
    };
  },
  props: {
    navigation: {
      type: Object,
    },
  },
  mounted(){
      this.result = this.navigation.getParam('calcResult');
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
