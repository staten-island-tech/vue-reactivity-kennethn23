<template>
  <div>
    <h1 v-if="test === true">Good</h1>
    <h1 v-else>Bad</h1>
  </div>
</template>

<script setup>
const test = false;
</script>

<style scoped>

</style>