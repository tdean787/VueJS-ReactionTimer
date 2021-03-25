<template>
  <div @click="stopTimer" class="block" v-if="showBlock">
    Click Me
  </div>
</template>

<script>
export default {
  name: "Block",
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      this.$emit("reactTime", this.reactionTime);
      clearInterval(this.timer);
      this.showBlock = !this.showBlock;
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: green;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
