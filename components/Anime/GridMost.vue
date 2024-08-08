<script setup>
const { anime, pages, title, destination } = defineProps({
  anime: Object,
  pages: Array,
  title: String,
  destination: String,
})
</script>
<template>
  <main>
    <h1
      class="text-5xl my-5 px-10 font-semibold font-mina w-full text-center md:text-start"
      id="grid-start"
    >
      {{ title }}
    </h1>
    <div
      class="grid grid-cols-2 place-content-center gap-4 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 2xl:grid-cols-5 px-2 lg:px-5"
    >
      <AnimeCard v-for="genre in anime.animes" :anime="genre" />
    </div>
    <div
      class="flex space-x-3 text-lg min-w-96 max-w-[70%] py-10 px-7 border-y border-ui-bg mx-auto overflow-auto"
    >
      <NuxtLink
        v-for="page in pages"
        :to="{
          name: destination,
          query: { page: page },
        }"
        class="transition duration-200 hover:text-complementary hover:-translate-y-1 focus:text-complementary focus:-translate-y-1 focus:outline-none"
        :class="{
          'text-primary -translate-y-1 font-bold': page == anime.currentPage,
        }"
        >{{ page }}</NuxtLink
      >
    </div>
  </main>
</template>
