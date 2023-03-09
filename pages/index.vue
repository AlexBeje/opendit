<template>
  <Searcher @update:filter="(newValue) => (filter = newValue)" />
  <Table :filter="filter" />
</template>

<script setup lang="ts">
/**
 * Variables
 * ---------
 */
const filter = ref<string>();
</script>
