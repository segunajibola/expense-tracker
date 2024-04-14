<template>
  <h3
    class="border-b-2 border-style-solid border-[#bbb] pb-[10px] text-2xl mt-[40px] mx-0 mb-[10px]"
  >
    Add new transaction
  </h3>
  <form id="form" class="text-xl" @submit.prevent="onSubmit">
    <div class="flex gap-10">
      <div class="flex gap-1 text-xl">
        <input type="radio" id="income" name="transaction" v-model="isIncome" />
        <label for="income">Income</label>
      </div>

      <div class="flex gap-1 text-xl">
        <input
          type="radio"
          id="expenses"
          name="transaction"
          v-model="isExpense"
        />
        <label for="income">Expenses</label>
      </div>
    </div>
    <div class="form-control">
      <label for="text" class="my-2 inline-block">Text</label>
      <input
        type="text"
        id="text"
        placeholder="Enter text..."
        v-model="text"
        class="border border-solid border-[#dedede] rounded-[2px] block text-[16px] p-2.5 w-full"
      />
    </div>
    <div class="form-control">
      <label for="amount" class="my-2 inline-block">Amount <br /> </label>
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
        class="border border-solid border-[#dedede] rounded-[2px] block text-[16px] p-2.5 w-full focus:outline-0"
      />
    </div>
    <button
      class="btn cursor-pointer bg-[#5036d1] text-[#fff] border-none block text-[20px] mt-2.5 mb-7.5 p-2.5 w-full hover:bg-[#230e8b]"
    >
      Add transaction
    </button>
  </form>
</template>

<script setup>
import { useToast } from "vue-toastification";
import { ref } from "vue";

const text = ref("");
const amount = ref("");
const isExpense = ref(false);
const isIncome = ref(false);

const toast = useToast();

const emit = defineEmits(["transactionSubmitted"]);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("Text and Amount inputs must be filled.");
    return;
  }

  if (!isExpense.value && !isIncome.value) {
    toast.error("Please select either Income or Expenses.");
    return;
  }

  const transactionData = {
    text: text.value,
    amount:
      parseFloat(amount.value) *
      (isExpense.value === "on" ? -1 : isIncome.value === "on" ? 1 : ""),
  };

  emit("transactionSubmitted", transactionData);

  text.value = "";
  amount.value = "";
};
</script>
