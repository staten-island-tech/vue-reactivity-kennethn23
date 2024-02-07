<template>
    <div class="itemCard">
        <h1>{{ Option.name }}</h1>
        <h2>{{ Option.description }}</h2>
        <h3>${{ Option.price }}</h3>
        <h3>{{ counter }}</h3>
        <button @click="addToCart">Add</button>
        <button @click="removeFromCart">Remove</button>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const props = defineProps({
    Option: Object,
});
const counter = ref(0);
const emit = defineEmits(['response']);

function addToCart () {
    counter.value++;
    emit('response', props.Option, "add");
}

function removeFromCart () {
    counter.value += -1;
    emit('response', props.Option, "remove");
}

</script>

<style scoped>

.itemCard {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 28vw;
    height: 28vh;
    text-align: center;
    background-color: rgba(0, 0, 0, 0.2);
    margin-bottom: 1vh;
    justify-content: space-evenly;
}

</style>