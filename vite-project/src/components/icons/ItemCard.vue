<template>
    <div>
        <h1>{{ Option.name }}</h1>
        <h2>{{ Option.description }}</h2>
        <h3>${{ Option.price }}</h3>
        <button @click="addToCart">Add to cart</button>
    </div>
</template>

<script setup>

const props = defineProps({
    Option: Object,
});

const emit = defineEmits(['response']);

function addToCart () {
    emit('response', props.Option);
}

</script>

<style scoped></style>