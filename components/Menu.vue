<template>
  <div class="flex flex-col gap-4 items-center mt-8">
    <el-button
      size="large"
      class="w-12 m-0"
      v-for="menuItem in menuItems"
      :color="menuItem.selected ? '#E7E7E7' : '#fff'"
    >
      <component :is="menuItem.icon" class="w-6" />
    </el-button>
  </div>
</template>

<script setup lang="ts">
import { HomeFilled, UserFilled } from '@element-plus/icons-vue';

/**
 * Variables
 * ---------
 */
const menuItems = [
  {
    icon: HomeFilled,
    selected: true,
  },
  {
    icon: UserFilled,
    selected: false,
  },
];
</script>

<style scoped lang="scss">
// removes the auto margin done by Element UI when 2 or more buttons are side by side
.el-button {
  margin: 0 !important;
}
</style>
