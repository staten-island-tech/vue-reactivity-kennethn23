<template>
    <div>
        <h1>You bought {{ Option.purchaseCount}} {{ Option.name }}s!</h1>
        <h2>${{ Option.purchaseCount * Option.price }}</h2>
        <h3>{{ flavorText }}</h3>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const props = defineProps({
    Option: Object,
});

let flavorText;

if (props.Option.purchaseCount == 0) {
    flavorText = ref(props.Option.noBuy);
} else {
    flavorText = ref(props.Option.buy);
}

</script>

<style scoped></style>