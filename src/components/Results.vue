<template>
  <h1>Result...</h1>
  <p>Your reaction time was {{ score }} ms</p>
</template>

<script>
export default {
  name: "Result",
  props: ["playing", "score"],
};
</script>
