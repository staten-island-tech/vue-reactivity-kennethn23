<template>
    <div>
        <h1>{{ Option.result }} {{ Option.purchaseCount }} {{ Option.unit }}!</h1>
        <h2>${{ Option.purchaseCount * Option.price }}</h2>
        <h3>{{ flavorText }}</h3>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const props = defineProps({
    Option: Object,
});

const flavorText = ref();

if (props.Option.purchaseCount == 0) {
    flavorText.value = props.Option.noBuy;
} else {
    flavorText.value = props.Option.buy;
}

</script>

<style scoped></style>