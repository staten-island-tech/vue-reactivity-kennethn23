<template>
    <div class="company">
      <h1>{{ currentCompany.name }}</h1>
      <h2>{{ currentCompany.initial }}</h2>
      <h3>{{ currentCompany.change }}</h3>
    </div>
  </template>

<script setup>
import { currentCompany } from '@/components/icons/DestCard.vue';



</script>

<style scoped></style>