<template>
  <h3
    class="border-b-2 border-style-solid border-[#bbb] text-lg pb-[10px] mt-[40px] mx-0 mb-[10px]"
  >
    History
  </h3>
  <ul id="list" class="list-none px-3">
    <li
      v-for="transaction in transactions"
      :key="transaction.id"
      :class="{
        'flex bg-[#fff] text-[#333] justify-between relative p-2.5 my-2.5 border-r-[5px] border-solid': true,
        'border-[#c0392b]': transaction.amount < 0,
        'border-[#2ecc71]': transaction.amount >= 0,
      }"
    >
      {{ transaction.text }} <span>${{ transaction.amount }}</span
      ><button
        class="delete-btn bg-[#e74c3c] cursor-pointer border-none text-[#fff] text-xl py-.5 px-1 absolute top-[50%] left-0 opacidty-0 hover:opacity-100 focus:outline-0"
        @click="deleteTransaction(transaction.id)"
      >
        x
      </button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["transactionDeleted"]);

const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};
</script>
