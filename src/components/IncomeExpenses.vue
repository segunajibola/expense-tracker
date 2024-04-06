<template>
  <div
    class="inc-exp-container bg-[#fff] p-5 flex justify-between my-5 mx-0 text-center"
  >
    <div class="flex flex-col w-[50%] border-r-2 border-solid border-[#dedede]">
      <h4>Income</h4>
      <p id="money-plus" class="text-[20px] tracking-wider my-1 mx-0 text-[#2ecc71]">+${{ income }}</p>
    </div>
    <div class="flex flex-col w-[50%]">
      <h4>Expense</h4>
      <p id="money-minus" class="text-[20px] tracking-wider my-1 mx-0 text-[#c0392b]">-${{ expenses }}</p>
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
