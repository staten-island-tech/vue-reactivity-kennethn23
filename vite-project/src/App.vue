<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>Spend a Billion dollars!</h1>
    </div>
  </header>

  <div class="view">
    <RouterView />
  </div>
</template>

<style scoped>

.view {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.wrapper {
  display: flex;
  justify-content: center;
}

h1 {
  font-size: 5vh;
}

</style>
