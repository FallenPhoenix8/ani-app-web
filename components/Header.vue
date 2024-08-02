<script setup>
const { homePageAnime } = defineProps({
  "home-page-anime": Object,
})

console.log(homePageAnime)

const spotlightAnimes = homePageAnime.spotlightAnimes
console.log(spotlightAnimes)

const currentSpotlightAnime = ref(spotlightAnimes[0])

const index = ref(1)

function circleSpotlight(index) {
  setInterval(() => {
    currentSpotlightAnime.value = spotlightAnimes[index]
    if (index != spotlightAnimes.length - 1) {
      index++
    } else {
      index = 0
    }
  }, 7000)
}
circleSpotlight(index.value)

function changeActiveSpotlight(index, newSpotlightIndex) {
  index = newSpotlightIndex - 1
  currentSpotlightAnime.value = spotlightAnimes[index]
}
</script>
<template>
  <header>
    <div
      id="spotlight-anime"
      class="relative overflow-x-hidden w-full min-w-full"
    >
      <ClientOnly>
        <SpotlightAnime
          :spotlight-anime="currentSpotlightAnime"
          :count="spotlightAnimes.length"
          @change:activeSpotlight="
            (newSpotlightIndex) =>
              changeActiveSpotlight(index, newSpotlightIndex)
          "
        />
      </ClientOnly>
    </div>
  </header>
</template>
