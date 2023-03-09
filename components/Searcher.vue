<template>
  <div class="w-full sm:max-w-sm flex gap-6 ml-auto">
    <el-input
      placeholder="Search"
      :prefix-icon="Search"
      v-model="filter"
      @input="$emit('update:filter', filter)"
      ref="input"
    />
    <el-button type="primary" color="#000" round>
      Add New<el-icon class="el-icon--right"><Plus /></el-icon>
    </el-button>
  </div>
</template>

<script setup lang="ts">
import { Plus, Search } from '@element-plus/icons-vue';

/**
 * Variables
 * ---------
 */
const filter = ref<string>();
</script>
