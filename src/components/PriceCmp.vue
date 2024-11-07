<script setup>
import { inject } from 'vue'
import { Currencies, ExchangeRate } from '@/const/const.js'

const currency = inject('currency')
const props = defineProps(['price'])

const formatPrice = (price) => {
  if (currency.value == Currencies.DOLLAR) {
    return `$${price}.00`
  }
  if (currency.value == Currencies.EURO) {
    return `€${price * ExchangeRate}`
  }
}
</script>
<template>
  <span>{{ formatPrice(props.price) }}</span>
</template>
<style scoped></style>
