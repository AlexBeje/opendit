<template>
  <div class="flex gap-4 justify-end">
    <Searcher @update:filter="(newValue) => (filter = newValue)" />
    <AddNew />
  </div>
  <Table :filter="filter" />
</template>

<script setup lang="ts">
/**
 * Variables
 * ---------
 */
const filter = ref<string>();
</script>
