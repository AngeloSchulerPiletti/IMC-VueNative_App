<template>
  <app-navigator></app-navigator>
</template>

<script>
import { createAppContainer, createStackNavigator } from "vue-native-router";
import Welcome from "./pages/Welcome.vue";
import Calculate from "./pages/Calculate.vue";
import Result from "./pages/Result.vue";

const StackNavigator = createStackNavigator(
  {
    Welcome: Welcome,
    Calculate: Calculate,
    Result: Result,
  },
  {
    initialRouteName: "Welcome",
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },
};
</script>

<style>

</style>
