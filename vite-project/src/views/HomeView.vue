<template>
  <div>
    <DestCard v-for="company in prices"
    :key="company.name"
    :Company="company"
    />
  </div>
</template>

<script setup>
import DestCard from '@/components/icons/DestCard.vue';
import { prices } from '@/stores/prices';
</script>

<style scoped>

h1 {
  color: red
}
</style>