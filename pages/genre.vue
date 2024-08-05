<script setup>
useHead({
  bodyAttrs: {
    class: "bg-bgColor overflow-x-hidden text-white",
  },
  htmlAttrs: {
    class: "scroll-smooth no-scrollbar",
  },
})

const genre = ref("")
const page = ref(() => useRoute().query.page)
const genreAnime = ref(undefined)
const genreKebabCase = ref("")
const pages = ref([])

async function updateGenres() {
  genreKebabCase.value = useRoute().query.genre
  page.value = useRoute().query.page

  genreKebabCase.value = genreKebabCase.value.replace(" ", "-")
  genreKebabCase.value = genreKebabCase.value.toLowerCase()

  await fetch(
    `http://193.150.21.20:3004/anime/genre/${genreKebabCase.value}?page=${page.value}`
  )
    .then((res) => res.json())
    .then((data) => {
      genreAnime.value = data

      pages.value = []

      for (let i = 1; i <= genreAnime.value.totalPages; i++) {
        pages.value.push(i)
      }
    })
    .catch((err) => console.error(err))
  document.documentElement.scrollTo({
    top: 0,
    behavior: "smooth",
  })
}

onMounted(() => {
  updateGenres()
})

watch(
  () => useRoute().query,
  () => {
    updateGenres()
  }
)
</script>
<template>
  <NavBar :genres="genreAnime.genres" v-if="genreAnime" />
  <GenreAnimesGrid :genre-anime="genreAnime" v-if="genreAnime" :pages="pages" />
</template>
