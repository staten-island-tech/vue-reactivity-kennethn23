<template>
    <div>
        <h1>{{ Company.name }}</h1>
        <h2>{{ Company.initial }}</h2>
        <h3>{{ Company.change }}</h3>
    </div>
        <a href="/company">Click me</a>
    <!-- <a :href="link">click me</a> -->
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    Company: Object,
});

/* const link = ref("/");
function getLink () {
    link.value = `/${ props.Company.name }`;
}
getLink(); */

const currentCompany = props.Company;
</script>

<style scoped></style>