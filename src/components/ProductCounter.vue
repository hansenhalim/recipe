<template>
  <div class="rounded-xl bg-sky-200 px-2 pb-1 pt-2 shadow dark:bg-cyan-800 dark:text-cyan-100">
    <div class="text-sm">{{ name }}</div>
    <div class="mt-2 flex font-light">
      <button
        @click="$emit('subClick')"
        :class="{ hidden: count <= 0 }"
        class="flex h-8 w-8 items-center justify-center rounded-full text-2xl active:bg-sky-300 dark:active:bg-cyan-700"
      >
        &minus;
      </button>
      <div :class="{ 'text-center': count > 0 }" class="grow text-3xl">
        {{ count }}
      </div>
      <button
        @click="$emit('addClick')"
        class="flex h-8 w-8 items-center justify-center rounded-full text-2xl active:bg-sky-300 dark:active:bg-cyan-700"
      >
        &plus;
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps(['name', 'count'])
</script>
