<template>
  <el-button v-if="pending" disabled class="sm: mt-4">Loading ...</el-button>
  <el-button v-else @click="loadTenMoreItems" class="sm: mt-4">Load more</el-button>
  <ul class="mt-4 p-4 border-gray-300 border-[1px]">
    <li v-for="product in data?.products">{{ product.title }}</li>
  </ul>
</template>

<script setup lang="ts">
interface Product {
  stock: string;
  title: string;
  brand: string;
  category: string;
  price: string;
  rating: string;
}

// Fetch data
const page = ref(10);
const { pending, refresh, error, data } = await useFetch<{
  products: Product[];
}>(() => `https://dummyjson.com/products?limit=${page.value}`);

/**
 * Fetch the next 10 items of the dummyjson product list
 */
function loadTenMoreItems() {
  if (data.value?.products.length === 100 || error.value) {
    return;
  }

  page.value += 10;
  refresh();
}
</script>
