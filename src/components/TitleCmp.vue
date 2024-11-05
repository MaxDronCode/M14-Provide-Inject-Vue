<script setup>
import { ref } from 'vue'

const title = ref('Snazzy Burger')

const emit = defineEmits(['placeOrder'])

const placeOrder = () => {
    emit('placeOrder', title.value)
}
</script>

<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <input v-model="title" />
    <button @click="placeOrder">Place Order</button>
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
</style>
