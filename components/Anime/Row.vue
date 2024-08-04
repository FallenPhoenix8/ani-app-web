<script setup>
const { animes, title } = defineProps({
  animes: Array,
  title: String,
})
</script>
<template>
  <div :id="$attrs.id" class="flex flex-col">
    <h2 class="max-w-md">{{ title }}</h2>
    <div
      class="flex mb-5 space-x-10 lg:space-x-7 overflow-x-auto max-w-none no-scrollbar"
    >
      <AnimeCard v-for="anime in animes" :anime="anime" :key="anime" />
      <div class="w-5"></div>
    </div>
  </div>
</template>
