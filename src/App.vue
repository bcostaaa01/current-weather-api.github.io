<template>
  <div>
    <WeatherComponent />
    <img
      src="https://www.pixel4k.com/wp-content/uploads/2018/09/canal-buildings-bridge-amsterdam-keizersgracht-4k_1538066402.jpg"
      alt=""
      style="width: 100%"
    />
  </div>
</template>

<script>
import WeatherComponent from "./components/WeatherComponent.vue";

export default {
  name: "App",
  components: {
    WeatherComponent,
  },
};
</script>

<style>
#app {
  font-family: 'roboto-mono', Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
