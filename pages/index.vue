<script setup>
useHead({
  bodyAttrs: {
    class: "bg-bgColor overflow-x-hidden text-white",
  },
})

let homePageAnime = undefined
await fetch("http://luka.lafp.cc:3004/anime/home")
  .then((res) => res.json())
  .then((data) => {
    homePageAnime = data
  })
  .catch((err) => {
    console.error(err)
  })
</script>

<template>
  <NavBar />
  <Header v-if="homePageAnime" :home-page-anime="homePageAnime" />
</template>
