<template>
    <div class="title">
        <h1>You've just spent <span :class="globalVariables.costColor.value">${{ globalVariables.totalCost.value.toLocaleString() }}</span>!</h1>
        <h2>Let's see what you've done...</h2>
        <RouterLink :to="{ path: '/'}">Go back</RouterLink>
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

.title {
    display: flex;
    flex-direction: column;
    align-items: center;
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