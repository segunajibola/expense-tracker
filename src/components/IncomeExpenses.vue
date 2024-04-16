<template>
  <div
    class="inc-exp-container bg-[#5036d1] p-5 flex justify-between my-5 mx-8 rounded-xl shadow-md text-center gap-2"
  >
    <div
      class="flex flex-col w-[50%] bg-slate-200 text-xl border-r-4 border-solid border-[#5036d1] rounded-2xl"
    >
      <h4>Income</h4>
      <p id="money-plus" class="tracking-wider my-1 mx-0 text-[#2ecc71]">
        +${{ income }}
      </p>
    </div>
    <div class="flex flex-col w-[50%] bg-slate-200 text-xl rounded-2xl">
      <h4>Expense</h4>
      <p
        id="money-minus"
        :class="{
          'tracking-wider my-1 mx-0': true,
          'text-[#c0392b]': props.expenses < 0,
        }"
      >
        {{ parsedExpenseFunc() }}
      </p>
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

const parsedExpenseFunc = () => {
  let parsedExpenses;
  if (props.expenses === 0) {
    parsedExpenses = "No expenses";
    return parsedExpenses;
  } else {
    parsedExpenses = parseInt(props.expenses.toString().substring(1), 10);
    return `-$${parsedExpenses}`;
  }
};
</script>
