<template>
    <div>
        <h1>{{ Company.name }}</h1>
        <h2>{{ Company.initial }}</h2>
        <h3>{{ Company.change }}</h3>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const props = defineProps({
    Company: Object,
});



</script>

<style scoped></style>