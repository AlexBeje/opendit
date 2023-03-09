<template>
  <div v-infinite-scroll="loadTenMoreItems" class="mt-4">
    <el-table ref="tableRef" :data="tableData" style="width: 100%">
      <el-table-column prop="stock" label="Stock" width="80">
        <template #default="scope">
          <ShoppingCart
            :class="`m-auto p-1 rounded-full w-6 
              ${setStockColor(scope.row.stock)}`"
            color="black"
          />
        </template>
      </el-table-column>
      <el-table-column prop="title" label="Title" />
      <el-table-column prop="brand" label="Brand" />
      <el-table-column prop="category" label="Category" />
      <el-table-column prop="price" label="Price" />
      <el-table-column prop="rating" label="Rating">
        <template #default="scope">
          {{ getRatingPercentage(scope.row.rating) }}%
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script setup lang="ts">
import { Product } from './Table.type';
import { ShoppingCart } from '@element-plus/icons-vue';

/**
 * Props
 * -----
 */
interface TableProps {
  filter: string | undefined;
}
const props = defineProps<TableProps>();
const { filter } = toRefs(props);

/**
 * Variables
 * ---------
 */
// const filter = ref<string>();
const page = ref(10);
const { refresh, error, data } = await useFetch<{
  products: Product[];
}>(() => `https://dummyjson.com/products?limit=${page.value}`);

/**
 * Computed Props
 * --------------
 */
const tableData = computed(() => {
  if (filter.value) {
    return data.value?.products.filter((product) =>
      product.title.toUpperCase().includes(filter.value?.toUpperCase() || '')
    );
  }
  return data.value?.products;
});

/**
 * Methods
 * -------
 */

/**
 * Fetch the next 10 items of the dummyjson product list
 */
const loadTenMoreItems = () => {
  if (data.value?.products.length === 100 || error.value) {
    return;
  }
  page.value += 10;
  refresh();
};

/**
 * Sets the stock color based on the stock value
 * @param stock
 * @returns {string | undefined}
 */
const setStockColor = (stock: number): string | undefined => {
  if (stock >= 100) {
    return 'bg-[#99FF99]';
  } else if (stock >= 50 && stock < 100) {
    return 'bg-[#FFF580]';
  } else if (stock < 50) {
    return 'bg-[#FFBDD1]';
  }
};

/**
 * Gets the percentage of the rating in the base of 5
 * @param rating
 */
const getRatingPercentage = (rating: number) => {
  return ((rating / 5) * 100).toFixed(1);
};
</script>