<template>
  <div id="app">
    <h1>vue-svg-ripple</h1>
    <SvgRipple
			ref="svg"
      image="./assets/img/img02.jpg"
      :distance="680"
      :depth="80"
      :duration="1.8"
      ease="Power3.easeOut"
      :isClick="true"
    />
  </div>
</template>

<script>
import dat from "dat.gui";
import SvgRipple from "./components/SvgRipple.vue";

export default {
  name: "app",
  components: {
    SvgRipple
  },

  mounted() {
    let gui = new dat.GUI({ autoPlace: false });
    gui.domElement.style.position = "fixed";
    gui.domElement.style.top = "0";
    gui.domElement.style.right = "0";
    document.body.appendChild(gui.domElement);

		let params = {
			easeList: [
				"Power0.easeNone",
				"Power1.easeIn",
				"Power1.easeInOut",
				"Power1.easeOut",
				"Power2.easeIn",
				"Power2.easeInOut",
				"Power2.easeOut",
				"Power3.easeIn",
				"Power3.easeInOut",
				"Power3.easeOut",
				"Power4.easeIn",
				"Power4.easeInOut",
				"Power4.easeOut",
				"Back.easeIn",
				"Back.easeOut",
				"Back.easeInOut",
				"Elastic.easeIn",
				"Elastic.easeOut",
				"Elastic.easeInOut",
				"Bounce.easeIn",
				"Bounce.easeOut",
				"Bounce.easeInOut",
				"Circ.easeIn",
				"Circ.easeOut",
				"Circ.easeInOut",
				"Expo.easeIn",
				"Expo.easeOut",
				"Expo.easeInOut",
				"Sine.easeIn",
				"Sine.easeOut",
				"Sine.easeInOut",
			]
		};

		gui.add(this.$refs.svg, "distance", 100, 1000);
		gui.add(this.$refs.svg, "depth", 10, 500);
		gui.add(this.$refs.svg, "duration", 0.1, 3.0);
		gui.add(this.$refs.svg, "ease", params.easeList);
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
