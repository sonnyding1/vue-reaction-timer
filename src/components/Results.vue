<template>
  <div class="results">
    <p v-if="score">Your reaction time: {{ score }}ms</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style></style>
