<script setup>
import { Currencies, ExchangeRate } from '@/const/const.js'

const props = defineProps(['sendProducts', 'currency'])

const emit = defineEmits(['saveProduct'])
const saveProduct = (productName) => {
  emit('saveProduct', productName)
}

const formatPrice = (price) => {
  if (props.currency.value == Currencies.DOLLAR) {
    return `$${price}.00`
  }
  if (props.currency.value == Currencies.EURO) {
    return `€${price * ExchangeRate}`
  }
}
console.log(`Desde product: ${props.products}`)
</script>
<template>
  <ul>
    <li v-for="product in props.sendProducts" :key="product.name">
      {{ product.name }}{{ formatPrice(product.price) }}
      <button @click="saveProduct(product.name)">Add to Cart</button>
    </li>
  </ul>
</template>
<style scoped></style>
