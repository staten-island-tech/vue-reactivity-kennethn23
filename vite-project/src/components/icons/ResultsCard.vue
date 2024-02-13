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
cardArray.value.sort((a, b) => b.purchaseCount - a.purchaseCount);
console.log(cardArray);
const cardIndex = ref(0);

const flavorText = ref();
const cardColor = ref("noBuy");

cardLogic();

function cardLogic () {
    if (cardArray.value[cardIndex.value].purchaseCount == 0) {
        flavorText.value = cardArray.value[cardIndex.value].noBuy;
        cardColor.value = "noBuy";
    } else if (cardArray.value[cardIndex.value].purchaseCount >= 30) {
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
    width: 6vh;
    height: 6vh;
    border-radius: 3vh;
    border: 0;
    transition: all 0.5s;
    font-size: 2vh;
}

button:hover {
    transform: scale(1.2);
}

.contents {
    display: flex;
    align-items: center;
    width: 100vh;
    justify-content: space-evenly;
}

img {
    width: 60%;
    height: 60%;
    margin-top: 3vh;
}

#noBuy {
    background-color: #23395B;
    color: white;
}
#buy {
    background-color: #406E8E;
    color: black;
}
#overBuy {
    background-color: #8EA8C3;
    color: black;
}

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 80vh;
    height: 60vh;
    margin-bottom: 5vh;
    justify-content: space-evenly;
    border-radius: 5vh;
    padding: 2vh;
    text-align: center;
}

@media screen and (max-width: 1000px) {
    .contents {
        width: 70vh;
    }

    .card {
        width: 50vh;
        height: 50vh;
    }
}

</style>