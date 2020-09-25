<template>
  <div class="auto-write">
    <h1>{{ displayText }}</h1>
  </div>
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
  },
  data() {
    return {
      autoWriteText: "",
      displayText: "",
      index: 0,
      delayTime: 0,
    };
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
.auto-write {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #17b85a;
  margin-top: 60px;
}
</style>
