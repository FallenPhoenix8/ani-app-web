<script setup>
useHead({
  bodyAttrs: {
    class: "bg-bgColor overflow-x-hidden text-white",
  },
})

let homePageAnime = undefined

await useFetch("http://luka.lafp.cc:3004/anime/home").then(
  (data) => (homePageAnime = data.data.value)
)
</script>

<template>
  <NavBar :genres="homePageAnime.genres" />
  <Header v-if="homePageAnime" :home-page-anime="homePageAnime" />
</template>
