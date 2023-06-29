<template>
  <div>Hook</div>
</template>

<script setup>
import { onBeforeMount, onBeforeUnmount, onMounted, onUnmounted } from '@vue/runtime-core';

onBeforeMount(() => {
  console.log('onBeforeMount');
});
onMounted(() => {
  console.log('onMounted');
});
onBeforeUnmount(() => {
  console.log('onBeforeUnmount');
});
onUnmounted(() => {
  console.log('onUnmounted');
});
</script>