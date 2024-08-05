<script setup>
const { genreAnime, pages } = defineProps({
  "genre-anime": Object,
  pages: Array,
})
</script>
<template>
  <main>
    <h1
      class="text-5xl my-5 px-10 font-semibold font-mina w-full text-center md:text-start"
      id="grid-start"
    >
      {{ genreAnime.genreName }}
    </h1>
    <div
      class="grid grid-cols-2 place-content-center gap-4 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 2xl:grid-cols-5 px-2 lg:px-5"
    >
      <AnimeCard v-for="genre in genreAnime.animes" :anime="genre" />
    </div>
    <div
      class="flex space-x-3 text-lg min-w-96 max-w-[70%] py-10 px-7 border-y border-ui-bg mx-auto overflow-auto"
    >
      <NuxtLink
        v-for="page in pages"
        :to="{
          name: 'genre',
          query: { genre: useRoute().query.genre, page: page },
        }"
        class="transition duration-200 hover:text-complementary hover:-translate-y-1 focus:text-complementary focus:-translate-y-1 focus:outline-none"
        :class="{
          'text-primary -translate-y-1 font-bold':
            page == genreAnime.currentPage,
        }"
        >{{ page }}</NuxtLink
      >
    </div>
  </main>
</template>
