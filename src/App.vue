<template>
  <div id="app">
    <h1>vue-svg-ripple</h1>
		<SvgRipple image="./assets/img/img02.jpg" :distance="680"  :depth="80" :duration="1.8" ease="Power3.easeOut" :isClick="true" />
  </div>
</template>

<script>
import SvgRipple from "./components/SvgRipple.vue";

export default {
  name: "app",
  components: {
    SvgRipple
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
svg {
  width: 640px;
  height: 360px;
  cursor: pointer;
}
</style>
