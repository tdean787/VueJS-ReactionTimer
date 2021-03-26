<template>
  <h1>Result...</h1>
  <p>Your reaction time was {{ score }} ms</p>
  <p>{{ resultText }}</p>
</template>

<script>
export default {
  name: "Result",
  props: ["score"],
  data() {
    return {
      resultText: "",
    };
  },
  mounted() {
    if (this.score <= 160) {
      this.resultText = "Not bad! Faster than average";
    } else if (this.score <= 225) {
      this.resultText = "About average reaction speed";
    } else if (this.score <= 325) {
      this.resultText = "A little bit slower than average reaction time";
    } else {
      this.resultText = "....give it another go";
    }
  },
};
</script>
