<template>
  <h3 class="border-b-2 border-style-solid border-[#bbb] pb-[10px] mt-[40px] mx-0 mb-[10px]">Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text" class="my-2 inline-block">Text</label>
      <input type="text" id="text" placeholder="Enter text..." v-model="text" class="border border-solid border-[#dedede] rounded-[2px] block text-[16px] p-2.5 w-full"/>
    </div>
    <div class="form-control">
      <label for="amount" class="my-2 inline-block"
        >Amount <br />
        (negative - expense, positive - income)</label
      >
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      class="border border-solid border-[#dedede] rounded-[2px] block text-[16px] p-2.5 w-full focus:outline-0"/>
    </div>
    <button class="btn cursor-pointer bg-[#9c88ff] text-[#fff] border-none block text-[16px] mt-2.5 mb-7.5 p-2.5 w-full">Add transaction</button>
  </form>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';

const text = ref('');
const amount = ref('');

// Get toast interface
const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error('Both fields must be filled.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit('transactionSubmitted', transactionData);

  // Clear form fields
  text.value = '';
  amount.value = '';
};
</script>
