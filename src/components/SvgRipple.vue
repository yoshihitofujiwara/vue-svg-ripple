/*==========================================================================
	template
==========================================================================*/
<template>
  <svg
		ref="svg"
		@click="click"
	>
    <filter id="ripple">
      <feImage
        xlink:href="./assets/img/ripple.png"
        :x="x"
        :y="y"
        :width="size"
        :height="size"
        result="ripple"
      ></feImage>
      <feDisplacementMap
        :scale="scale"
        in="SourceGraphic"
        in2="ripple"
        xChannelSelector="R"
        yChannelSelector="G"
        color-interpolation-filters="sRGB"
        result="dm"
      ></feDisplacementMap>
      <feComposite operator="in" in2="ripple"></feComposite>
      <feComposite in2="SourceGraphic"></feComposite>
    </filter>
    <g>
      <image
        :xlink:href="image"
        filter="url(#ripple)"
        width="100%"
        height="100%"
        x="0"
        y="0"
      ></image>
    </g>
  </svg>
</template>


/*==========================================================================
	script
==========================================================================*/
<script>
import { TweenLite } from "gsap/TweenMax";


export default {
  name: "SvgRipple",

  /**
   * @props
   */
  props: {
    image: {
      type: String,
      default: "../assets/img/img01.jpg"
    },
		distance: {
			type: Number,
      default: 512
		},
		depth: {
			type: Number,
      default: 100
		},
		duration: {
			type: Number,
      default: 1.8
		},
		ease: {
			type: [String, Object],
      default: "Power2.easeOut"
		},
		isClick: {
			type: Boolean,
      default: true
		}
  },

  /**
   * @data
   */
  data() {
    return {
      width: 0,
      height: 0,

			// @private
			size: 0,
			x: 0,
			y: 0,
			scale: 0,
			originX: 0,
			originY: 0,
			progress: 0,
    };
  },

  /**
   * @watch
   */
	watch:{
		progress(){
			this.scale = this.depth * (1 - this.progress);
			this.size = this.distance * this.progress;
			this.x = this.originX - this.size * 0.5;
			this.y = this.originY - this.size * 0.5;
		}
	},

  /**
   * @mounted
   */
  mounted() {
		if(this.width || this.height){
			let style = window.getComputedStyle(this.$refs.svg);
			this.width = this.width || +style.width.replace("px", "");
			this.height = this.height || +style.height.replace("px", "");
		}
  },

  /**
   * @methods
   */
  methods: {
		ripple(x, y){
			this.originX = x;
			this.originY = y;
			this.tween();
		},

		click(event){
			if(this.isClick){
				this.ripple(event.offsetX, event.offsetY);
			} else {
				this.$emit('click')
			}
		},

		tween(){
      TweenLite
			.fromTo(this, this.duration, {
        progress: 0,
			},{
        progress: 1,
        ease: this.ease,
      });
		}
	}
};
</script>


/*==========================================================================
	style
==========================================================================*/
<style scoped>
</style>
