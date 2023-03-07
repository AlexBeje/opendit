<template>
  <div class="w-full sm:w-1/2 flex gap-6 ml-auto">
    <el-input placeholder="Search" :prefix-icon="Search" />
    <el-button type="primary" color="#111E21">
      Add New<el-icon class="el-icon--right"><Plus /></el-icon>
    </el-button>
  </div>
</template>

<script setup lang="ts">
import { Plus, Search } from '@element-plus/icons-vue';
</script>
