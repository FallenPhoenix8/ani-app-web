<script setup>
const { homePageAnime } = defineProps({
  "home-page-anime": Object,
})
</script>
<template>
  <main class="relative lg:-mt-32 z-90 ml-5">
    <AnimeRow
      title="Trending"
      :animes="homePageAnime.trendingAnimes"
      id="trending"
    />
  </main>
</template>
