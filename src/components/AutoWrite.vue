<template>
  <div :class=" hasCustomClass ? getCssClassName : 'default-auto-write' " v-html="getDisplayText" />
</template>	

<script>
export default {
  name: "AutoWrite",
  props: {
    text: {
      type: String,
      required: true,
    },
    delay: {
      type: Number,
      default: 100,
    },
    tag: {
      type: String,
      default: "h1",
		},
		cssClass:{
			type: String,
		}
  },
  data() {
    return {
      autoWriteText: null,
      displayText: null,
      index: 0,
      delayTime: 0,
			tagName: null,
			hasCustomClass: false
    };
  },
  computed: {
    getDisplayText() {
      return `<${this.tagName}> ${this.displayText} </${this.tagName}>`;
		},
		getCssClassName(){
			return this.cssClass;
		}
  },
  mounted() {
    // update data property from props
    this.initData();

    // init writing
    setInterval(this.initWriting, this.delayTime);
  },
  methods: {
    initData() {
      this.autoWriteText = this.text;
      this.delayTime = this.delay;
			this.tagName = this.tag;
			
			// Check if cssClass prop exists
			if(this.cssClass){
				this.hasCustomClass = true;
			}
    },
    initWriting() {
      this.displayText = this.autoWriteText.slice(0, this.index);

      if (this.index > this.autoWriteText.length) {
        this.index = 0;
      }
      this.index++;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.default-auto-write {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #17b85a;
  margin-top: 60px;
}
</style>
