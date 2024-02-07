<template>
    <div>
        <h1>You've just spent ${{ route.params.totalCost }}!</h1>
        <h2>Let's see what you've done...</h2>
    </div>
    <div class="cardHolder">
        <ResultsCard v-for="option in options"
        :key="option.name"
        :Option="option"
        />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRoute } from 'vue-router';
import ResultsCard from '@/components/icons/ResultsCard.vue';
import { options } from '@/stores/options';

const route = useRoute();
const totalCost = ref(0);
totalCost.value = route.params.totalCost;

</script>

<style scoped></style>