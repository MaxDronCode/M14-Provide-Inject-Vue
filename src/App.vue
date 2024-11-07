<script setup>
import { ref, reactive, provide } from 'vue'
import products from '@/productsData/products.json'
import { Currencies } from '@/const/const.js'
import TitleCmp from '@/components/TitleCmp.vue'
import ProductCmp from '@/components/ProductCmp.vue'

const currency = ref(Currencies.DOLLAR)
provide('currency', currency)

const productsInCart = reactive([])

const receiveTitle = (title) => {
  alert(`Su pedido en ${title} se ha tramitado!`)
}

const saveProduct = product => {
  productsInCart.push(product)
  alert(productsInCart)
}

</script>

<template>
  <div class="general-container">
    <TitleCmp @placeOrder="receiveTitle"/>
    <div>
      <span>Currency</span>
      <select v-model="currency">
        <option>{{ Currencies.DOLLAR }}</option>
        <option>{{ Currencies.EURO }}</option>
      </select>
    </div>
      <ProductCmp :sendProducts="products" @saveProduct="saveProduct"/>
  </div>
</template>

<style scoped>
.general-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
</style>
