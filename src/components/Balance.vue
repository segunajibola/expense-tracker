<template>
  <h4 class="m-0 uppercase">Your Balance</h4>
  <h1 class="tracking-wider">${{ total }}</h1>
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
