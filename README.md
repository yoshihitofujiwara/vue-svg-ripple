# vue-svg-ripple

<img src="sample.gif" />

<ul>
	<li><a href="https://yoshihitofujiwara.github.io/vue-svg-ripple/index.html" target="_blank">DEMO</a></li>
</ul>


___
## Usage

```
<template>
  <div id="app">
    <h1>vue-svg-ripple</h1>
		<p><a href="https://github.com/yoshihitofujiwara/vue-svg-ripple" target="_blank">
			<SvgRipple image="../assets/img/img02.jpg" :distance="680"  :depth="80" :duration="1.8" ease="Power3.easeOut" :isClick="true"/>
		</a></p>
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
svg {
  width: 640px;
  height: 360px;
  cursor: pointer;
}
</style>

```

___
## Options

|name|type|default|description|
|----|----|----|----|
|image|String|undefined|<strong style="color:#f09">Required</strong> image path|
|distance|Number|512|Ripple Distance|
|depth|Number|100|Ripple Depth|
|duration|Number|0.8|Animation Duration (Sec)|
|ease|String, Object|Power2.easeOut|Animation Easing: <a href="https://greensock.com/docs/Easing" target="_blank">GreenSock Ease</a>|
|isClick|Boolean|true|Click To Ripple|
|click|event| | emit click |
___


## Project setup
yarn or npm

```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Run your tests
```
yarn run test
```

### Lints and fixes files
```
yarn run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
