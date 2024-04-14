<template>
  <div class="text-center">
    <h4 class="m-0 uppercase text-2xl font-semibold">Balance</h4>
    <h1 class="tracking-wide text-xl">${{ total }}</h1>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
