<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>Rob a Billionaire!</h1>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

.wrapper {
  display: flex;
  justify-content: center;
}

h1 {
  font-size: 5vh;
}

</style>
