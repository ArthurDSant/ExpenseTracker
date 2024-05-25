<template>
  <h3 class='addSectionTitle'>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="title">
      <label for="text">
        <p class="formTitles">
          Title
        </p>
      </label>
      <input type="text" id="text" placeholder="Enter the title here" v-model="text" />
    </div>
    
    <div class="amount">
      <label for="amount">
        <p class='formTitles'>
          Amount
        </p>
        <p class="description">
          (negative - expense, positive - income)
        </p>
      </label>
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div>

    <button class="btn-add">Add transaction</button>
  </form>
</template>




<script setup>
import './index.css'
import { ref } from 'vue';

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
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