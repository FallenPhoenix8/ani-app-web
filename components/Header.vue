<script setup>
const { homePageAnime } = defineProps({
  "home-page-anime": Object,
})

const spotlightAnimes = homePageAnime.spotlightAnimes

const currentSpotlightAnime = ref(spotlightAnimes[0])

const index = ref(1)
const headerInterval = ref(undefined)

const circleSpotlight = () => {
  const headerInterval = setInterval(() => {
    currentSpotlightAnime.value = spotlightAnimes[index.value]
    if (index.value != spotlightAnimes.length - 1) {
      index.value++
    } else {
      index.value = 0
    }
  }, 7000)
}

onMounted(() => {
  circleSpotlight()
})

function changeActiveSpotlight(newSpotlightIndex) {
  index.value = newSpotlightIndex - 1
  currentSpotlightAnime.value = spotlightAnimes[index.value]
  clearInterval(headerInterval)
}
</script>
<template>
  <header>
    <div
      id="spotlight-anime"
      class="relative overflow-x-hidden w-full min-w-full"
    >
      <SpotlightAnime
        :spotlight-anime="currentSpotlightAnime"
        :count="spotlightAnimes.length"
        @change:activeSpotlight="
          (newSpotlightIndex) => changeActiveSpotlight(newSpotlightIndex)
        "
      />
    </div>
  </header>
</template>
