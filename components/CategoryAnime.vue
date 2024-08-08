<script setup>
const { categoryName, destination } = defineProps({
  "category-name": String,
  destination: String,
})
useHead({
  bodyAttrs: {
    class: "bg-bgColor overflow-x-hidden text-white",
  },
  htmlAttrs: {
    class: "scroll-smooth no-scrollbar",
  },
})

const animeRes = ref(undefined)
const pages = ref([])
const page = ref(() => useRoute().query.page)

async function updateGenres() {
  page.value = useRoute().query.page

  await fetch(
    `http://193.150.21.20:3004/anime/${categoryName}?page=${page.value}`
  )
    .then((res) => res.json())
    .then((data) => {
      animeRes.value = data

      pages.value = []

      for (let i = 1; i <= animeRes.value.totalPages; i++) {
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
  <NavBar :genres="animeRes.genres" v-if="animeRes" />
  <AnimeGridMost
    :anime="animeRes"
    :pages="pages"
    :title="animeRes.category"
    :destination="destination"
    v-if="animeRes"
  />
</template>
