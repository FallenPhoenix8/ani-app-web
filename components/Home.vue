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
    <AnimeRow
      title="Latest Episode"
      :animes="homePageAnime.latestEpisodeAnimes"
      id="latest-episode"
    />
    <AnimeRow
      title="Latest Completed"
      :animes="homePageAnime.latestCompletedAnimes"
      id="latest-completed"
    />
    <AnimeRow
      title="Most Popular"
      :animes="homePageAnime.mostPopularAnimes"
      id="most-popular"
    />
    <AnimeRow
      title="Top Upcoming"
      :animes="homePageAnime.topUpcomingAnimes"
      :is-upcoming="true"
      id="top-upcoming"
    />
  </main>
</template>
