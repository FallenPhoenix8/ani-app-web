<script setup>
useHead({
  bodyAttrs: {
    class: "bg-bgColor overflow-x-hidden text-white",
  },
  htmlAttrs: {
    class: "scroll-smooth no-scrollbar",
  },
})

let homePageAnime = undefined

await useFetch("http://luka.lafp.cc:3004/anime/home").then(
  (data) => (homePageAnime = data.data.value)
)
</script>

<template>
  <NavBar v-if="homePageAnime" :genres="homePageAnime.genres" />
  <Header v-if="homePageAnime" :home-page-anime="homePageAnime" />
  <Home v-if="homePageAnime" :home-page-anime="homePageAnime" />
</template>
