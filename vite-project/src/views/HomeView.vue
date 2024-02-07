<template>
  <div class="optionList">
    <ItemCard v-for="option in options"
    :key="option.name"
    :Option="option"
    @response="updateCheckout"
    />
  </div>

  <div class="totalCheckout">
    <p><span :class="costColor">${{ totalCost }}</span> out of $1,000,000,000</p>
    <RouterLink :to="{ path: '/results/' + totalCost}">Done</RouterLink>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ItemCard from '@/components/icons/ItemCard.vue';
import { options } from '@/stores/options';

const totalCost = ref(0);
const costColor = ref("notFull");

function updateCheckout (item) {

  if (totalCost.value >= 1000000000) {
    return;
  }
  
  totalCost.value += item.price;
  const finder = ref(options.find((itemJS) => itemJS.name == item.name));
  finder._rawValue.purchaseCount++;

  if (totalCost.value > 1000000000) {
    costColor.value = "overflow";
  } else if (totalCost.value >= 900000000) {
    costColor.value = "full";
  } else if (totalCost.value >= 750000000) {
    costColor.value = "closeToFull";
  } else if (totalCost.value >= 500000000) {
    costColor.value = "middle";
  } else if (totalCost.value >= 250000000) {
    costColor.value = "start";
  }
}

</script>

<style scoped>

.notFull {
  color: rgb(123, 255, 0);
}

.start {
  color: rgb(251, 255, 0);
}

.middle {
  color: rgb(255, 208, 0);
}

.closeToFull {
  color: rgb(255, 102, 0);
}

.full {
  color: rgb(255, 0, 0);
}

.overflow {
  color: rgb(255, 0, 149);
}

</style>