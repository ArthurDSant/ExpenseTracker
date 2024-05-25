<template>
  <h4 class="totalTitle">Your Balance</h4>
  <h1 class="totalNumber">${{ total }}</h1>
</template>

<script setup>
import './index.css'
import { defineProps } from 'vue';

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>