<template>
  <el-button
    class="relative"
    type="primary"
    color="#000"
    round
    @click="dialogVisible = !dialogVisible"
  >
    Add New<el-icon class="el-icon--right"><Plus /></el-icon>
  </el-button>
  <div
    v-if="dialogVisible"
    class="absolute bg-white drop-shadow mt-10 rounded-lg shadow-lg text-xs w-[110px] z-10"
  >
    <p class="cursor-pointer p-3 rounded-tl-lg rounded-tr-lg hover:bg-gray-200" @click="dialogVisible = !dialogVisible">
      Add manually
    </p>
    <p class="cursor-pointer p-3 rounded-bl-lg rounded-br-lg hover:bg-gray-200" @click="dialogVisible = !dialogVisible">
      Import Excel
    </p>
  </div>
</template>

<script setup lang="ts">
import { Plus } from '@element-plus/icons-vue';

const dialogVisible = ref(false);
</script>
ç
