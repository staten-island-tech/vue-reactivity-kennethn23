<template>
  <div>
    <ItemCard v-for="company in prices"
    :key="company.name"
    :Company="company"
    />
  </div>
</template>

<script setup>

import ItemCard from '@/components/icons/ItemCard.vue';
import { prices } from '@/stores/options';



</script>

<style scoped></style>