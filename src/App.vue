<script setup>
import { ref, reactive } from 'vue'
import products from '@/productsData/products.json'
import { Currencies, ExchangeRate } from '@/const/const.js'

const title = ref('Snazzy Burger')
const currency = ref(Currencies.DOLLAR)
const productsInCart = reactive([])

const placeOrder = () => {
  alert(`Su pedido en ${title.value} se ha tramitado!`)
}

const formatPrice = (price) => {
  if (currency.value == Currencies.DOLLAR) {
    return `$${price}.00`
  }
  if (currency.value == Currencies.EURO) {
    return `€${price * ExchangeRate}`
  }
}

const addToCart = (product) => {
  productsInCart.push(product)
  alert(productsInCart)
}
</script>

<template>
  <div class="general-container">
    <h1>{{ title }}</h1>
    <input v-model="title" />
    <button @click="placeOrder">Place Order</button>
    <div>
      <span>Currency</span>
      <select v-model="currency">
        <option>{{ Currencies.DOLLAR }}</option>
        <option>{{ Currencies.EURO }}</option>
      </select>
    </div>
    <ul>
      <li v-for="product in products" :key="product.name">
        {{ product.name }}{{ formatPrice(product.price) }}
        <button @click="addToCart(product.name)">Add to Cart</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.general-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
</style>
