<template>
  <div v-infinite-scroll="loadTenMoreItems" class="mt-4">
    <el-table :data="data?.products" style="width: 100%">
      <el-table-column prop="stock" label="Stock" />
      <el-table-column prop="title" label="Title" />
      <el-table-column prop="brand" label="Brand" />
      <el-table-column prop="category" label="Category" />
      <el-table-column prop="price" label="Price" />
      <el-table-column prop="rating" label="Rating" />
    </el-table>
  </div>
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
const { refresh, error, data } = await useFetch<{
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
