<template>
  <h1 class="rank">Time: {{ score }} ms, you ware {{ rank }}</h1>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 150) {
      this.rank = "Wery fast";
    } else if (this.score < 250) {
      this.rank = "Fast";
    } else if (this.score < 400) {
      this.rank = "Medium";
    } else {
      this.rank = "Slow";
    }
  },
};
</script>
<style>
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>
