<template>
    <div class="contents">
        <button @click="previousCard">&lt;</button>
        <div class="card" :id="cardColor">
            <img :src="cardArray[cardIndex].img" :alt="cardArray[cardIndex].name">
            <h1>{{ cardArray[cardIndex].result }} {{ cardArray[cardIndex].purchaseCount.toLocaleString() }} {{ cardArray[cardIndex].unit }}!</h1>
            <h3>{{ flavorText }}</h3>
            <h2>${{ (cardArray[cardIndex].purchaseCount * cardArray[cardIndex].price).toLocaleString() }}</h2>
        </div>
        <button @click="nextCard">></button>
    </div>
</template>

<script setup>

import { ref } from 'vue';
import { options } from '@/stores/options';

const props = defineProps({
    Option: Object,
});

const cardArray = ref([...options]);
const cardIndex = ref(0);

const flavorText = ref();
const cardColor = ref("noBuy");

cardLogic();

function cardLogic () {
    if (cardArray.value[cardIndex.value].purchaseCount == 0) {
        flavorText.value = cardArray.value[cardIndex.value].noBuy;
        cardColor.value = "noBuy";
    } else if (cardArray.value[cardIndex.value].purchaseCount >= 10) {
        flavorText.value = cardArray.value[cardIndex.value].overBuy;
        cardColor.value = "overBuy";
    } else {
        flavorText.value = cardArray.value[cardIndex.value].buy;
        cardColor.value = "buy";
    }
}

function previousCard () {
    cardIndex.value += -1;
    if (cardIndex.value < 0) {
        cardIndex.value = cardArray.value.length - 1;
    }
    cardLogic();
}

function nextCard () {
    cardIndex.value++;
    if (cardIndex.value > cardArray.value.length - 1) {
        cardIndex.value = 0;
    }
    cardLogic();
}

</script>

<style scoped>

button {
    width: 4vh;
    height: 4vh;
    border-radius: 2vh;
    border: 0;
}

.contents {
    display: flex;
    align-items: center;
    width: 70vw;
    justify-content: space-evenly;
}

img {
    width: 60%;
    height: 60%;
    margin-top: 3vh;
}

#noBuy {
    background-color: red;
    color: white;
}
#buy {
    background-color: greenyellow;
    color: black;;
}
#overBuy {
    background-color: yellow;
    color: black;
}

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: red;
    width: 50vw;
    height: 70vh;
    margin-bottom: 5vh;
    justify-content: space-evenly;
}

</style>