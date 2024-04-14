<template>
  <div class="text-center">
    <h4 class="m-0 uppercase text-4xl font-semibold">Balance</h4>
    <h1 class="tracking-wide text-5xl">${{ total }}</h1>
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
