<template>
  <div class="totalCheckout">
    <p><span :class="costColor">${{ totalCost.toLocaleString() }}</span> out of $1,000,000,000</p>
    <RouterLink :to="{ path: '/results'}">Done</RouterLink>
  </div>

  <div class="optionList">
    <ItemCard v-for="option in options"
    :key="option.name"
    :Option="option"
    @response="updateCheckout"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ItemCard from '@/components/icons/ItemCard.vue';
import { options } from '@/stores/options';
import { globalVariables } from '@/stores/globalVariables';

const totalCost = globalVariables.totalCost;
const costColor = globalVariables.costColor;

function updateCheckout (item, type) {
  
  if (type == "add") {
    if (totalCost.value >= 1000000000) {
      return;
    }

    if (totalCost.value + item.price > 1000000000) {
      return;
    }

    totalCost.value += item.price;
    const finder = ref(options.find((itemJS) => itemJS.name == item.name));
    finder._rawValue.purchaseCount++;

  } else if (type == "remove") {
    totalCost.value += -(item.price);
    const finder = ref(options.find((itemJS) => itemJS.name == item.name));
    finder._rawValue.purchaseCount += -1;
  }

  if (totalCost.value >= 900000000) {
    costColor.value = "full";
  } else if (totalCost.value >= 750000000) {
    costColor.value = "closeToFull";
  } else if (totalCost.value >= 500000000) {
    costColor.value = "middle";
  } else if (totalCost.value >= 250000000) {
    costColor.value = "start";
  } else if (totalCost.value < 250000000) {
    costColor.value = "notFull";
  }
}

</script>

<style scoped>

.totalCheckout {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.optionList {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 100%;
}

.notFull {color: rgb(123, 255, 0)}
.start {color: rgb(251, 255, 0)}
.middle {color: rgb(255, 208, 0)}
.closeToFull {color: rgb(255, 102, 0)}
.full {color: rgb(255, 0, 0)}

</style>