<template>
  <div class="h-[72px] p-6 pl-10 shadow-gray-300/30 shadow-lg">
    {{ title }}
  </div>
</template>

<script setup lang="ts">
interface HeaderProps {
  title: string;
}

defineProps<HeaderProps>();
</script>
