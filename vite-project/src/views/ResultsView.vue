<template>
    <div class="title">
        <h2 class="counter">You've just spent <span :class="globalVariables.costColor.value">${{ globalVariables.totalCost.value.toLocaleString() }}</span></h2>
        <h3><RouterLink :to="{ path: '/'}">Go back</RouterLink></h3>
    </div>
    <div class="cardHolder">
        <ResultsCard/>
    </div>
</template>

<script setup>

import ResultsCard from '@/components/icons/ResultsCard.vue';
import { globalVariables } from '@/stores/globalVariables';

</script>

<style scoped>

.counter {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

.title {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgba(22, 25, 37, 0.6);
    width: 35vh;
    margin-bottom: 5vh;
    border-radius: 3vh;
}

.cardHolder {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.notFull {color: rgb(123, 255, 0)}
.start {color: rgb(251, 255, 0)}
.middle {color: rgb(255, 208, 0)}
.closeToFull {color: rgb(255, 102, 0)}
.full {color: rgb(255, 0, 0)}

</style>