<script setup>
import { Currencies, ExchangeRate } from '@/const/const.js'
import PriceCmp from '@/components/PriceCmp.vue';

const props = defineProps(['sendProducts'])

const emit = defineEmits(['saveProduct'])
const saveProduct = (productName) => {
  emit('saveProduct', productName)
}


const formatPrice = (price) => {
  if (props.currency == Currencies.DOLLAR) {
    return `$${price}.00`
  }
  if (props.currency == Currencies.EURO) {
    return `€${price * ExchangeRate}`
  }
}
</script>
<template>
  <ul>
    <li v-for="product in props.sendProducts" :key="product.name">
      {{ product.name }}
      <PriceCmp :price=product.price />
      <button @click="saveProduct(product.name)">Add to Cart</button>
    </li>
  </ul>
</template>
<style scoped></style>
