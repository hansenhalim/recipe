<template>
  <div class="relative flex flex-col items-center justify-center dark:text-emerald-100">
    <div class="absolute text-center">
      <div>{{ name }}</div>
      <div>{{ value }}</div>
    </div>
  </div>
</template>

<script setup>
defineProps(['name', 'value'])
</script>
