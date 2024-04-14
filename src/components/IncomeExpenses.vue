<template>
  <div
    class="inc-exp-container bg-[#fff] p-5 flex justify-between my-5 mx-0 text-center"
  >
    <div class="flex flex-col w-[50%] text-xl border-r-2 border-solid border-[#dedede]">
      <h4>Income</h4>
      <p id="money-plus" class="tracking-wider my-1 mx-0 text-[#2ecc71]">+${{ income }}</p>
    </div>
    <div class="flex flex-col w-[50%] text-xl">
      <h4>Expense</h4>
      <p id="money-minus" class="tracking-wider my-1 mx-0 text-[#c0392b]">-${{ parseInt(expenses.toString().substring(1), 10) }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>
