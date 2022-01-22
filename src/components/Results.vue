<template>
  <h2>Reaction time - {{ score }} ms</h2>
  <p class="pace">
    {{ pace }}
  </p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      pace: "",
    };
  },

  mounted() {
    if (this.score <= 250) {
      this.pace = "NINJA!!!";
    } else if (this.score <= 400) {
      this.pace = "Rapid Man!";
    } else {
      this.pace = "Snail pace...";
    }
  },
};
</script>

<style>
.pace {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
