<script setup>
import TheHeader from "@/components/TheHeader.vue";
import ProductCard from "@/components/ProductCard.vue";
import { useProductStore } from "@/stores/ProductStore";
import { useCartStore } from "@/stores/CartStore";


const productStore = useProductStore();
const cartStore = useCartStore();
productStore.fill();
const addToCart = (count, product) => {
  count = parseInt(count)
  for (let index = 0; index < count; index++) {
    cartStore.addProduct(product);

  }
}

</script>

<template>
  <div class="container">
    <TheHeader />
    <ul class="sm:flex flex-wrap lg:flex-nowrap gap-5">
      <ProductCard v-for="product in productStore.products" :key="product.name" :product="product"
        @addToCart="cartStore.items.push(product)" />
    </ul>
  </div>
</template>
