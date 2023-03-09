<template>
  <div class="w-full sm:w-[200px]">
    <el-input
      placeholder="Search"
      :prefix-icon="Search"
      v-model="filter"
      @input="$emit('update:filter', filter)"
      ref="input"
    />
  </div>
</template>

<script setup lang="ts">
import { Search } from '@element-plus/icons-vue';

/**
 * Variables
 * ---------
 */
const filter = ref<string>();
</script>
