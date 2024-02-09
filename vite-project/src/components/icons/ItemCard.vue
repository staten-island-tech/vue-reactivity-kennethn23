<template>
    <div class="itemCard">
        <h1>{{ Option.name }}</h1>
        <h2>{{ Option.description }}</h2>
        <h3>${{ Option.price.toLocaleString() }}</h3>
            <div class="buttons">
                <button class="add" @click="addToCart">+</button>
                <h3 id="counter">{{ counter.toLocaleString() }}</h3>
                <button class="remove" @click="removeFromCart">-</button>
            </div>
    </div>
</template>

<script setup>

import { ref } from 'vue';
import { globalVariables } from '@/stores/globalVariables';

const props = defineProps({
    Option: Object,
});
const counter = ref(props.Option.purchaseCount);
const emit = defineEmits(['response']);

function addToCart () {

    if (globalVariables.totalCost.value >= 1000000000) {
        return;
    }

    if (globalVariables.totalCost.value + props.Option.price > 1000000000) {
      return;
    }
    
    counter.value++;
    emit('response', props.Option, "add");
}

function removeFromCart () {
    if (counter.value == 0) {
        return;
    }

    counter.value += -1;
    emit('response', props.Option, "remove");
    console.log('a')
}

</script>

<style scoped>

.add {background-color: greenyellow}
.remove {background-color: red}

button {
    width: 4vh;
    height: 4vh;
    border-radius: 2vh;
    border: 0;
    transition: all 0.5s;
    font-size: 3vh;
}

button:hover {
    transform: scale(1.2);
}

#counter {
    width: 5vw;
}

.buttons {
    display: flex;
    align-items: center;
}

.itemCard {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 28vw;
    height: 40vh;
    text-align: center;
    background-color: rgba(0, 0, 0, 0.2);
    margin-bottom: 2vh;
    justify-content: space-evenly;
    border-radius: 5vh;
}

</style>