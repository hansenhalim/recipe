<template>
  <div class="relative flex flex-col items-center justify-center dark:text-emerald-100">
    <div class="absolute text-center">
      <div class="text-xs dark:text-white">{{ name }}</div>
      <div class="text-2xl font-light">{{ value }}</div>
    </div>
  </div>
</template>

<script setup>
defineProps(['name', 'value'])
</script>
