<template>
  <h3
    class="border-b-2 border-style-solid border-[#bbb] pb-[10px] mt-[40px] mx-0 mb-[10px]"
  >
    History
  </h3>
  <ul id="list" class="list-none p-0 mb-">
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
        class="delete-btn focus:outline-0"
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
