<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: "",
    };
  },
  mounted() {
    if (this.score < 250) return (this.rank = "Ninja fingers!");
    if (this.score < 500) return (this.rank = "Rapid reflexes!");
    else return (this.rank = "Snail pace...!");
  },
};
</script>

<style>
.rank {
  color: #0fe087;
  font-weight: bold;
}
</style>
