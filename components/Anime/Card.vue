<script setup>
const { anime, isUpcoming } = defineProps({
  anime: Object,
  isUpcoming: Boolean | null,
})
const description = ref("")
const episodes = ref({ sub: "", dub: "" })

async function fetchWithDelay() {}

onBeforeMount(async () => {
  if (!isUpcoming) {
    await $fetch(`http://193.150.21.20:3004/anime/info?id=${anime.id}`)
      // .then((res) => res.json())
      .then((data) => {
        episodes.value = data.anime.info.stats.episodes
        description.value = data.anime.info.description
      })
      .catch((err) => console.error(err))
  }
})
</script>
<template>
  <NuxtLink
    :to="`#`"
    class="group focus:outline-none hover:-translate-y-2 focus:-translate-y-2 transition duration-200 rounded-md cursor-pointer"
    v-if="isUpcoming"
  >
    <div class="rounded-md">
      <div class="relative min-h-52 rounded-md min-w-40">
        <div
          class="absolute w-full min-h-full max-w-40 max-h-full z-40 rounded-md bg-bgColor opacity-0 transition duration-300 hover:opacity-100 group-focus:opacity-100 hover:bg-opacity-70 group-focus:bg-opacity-70"
        >
          <h5
            class="line-clamp-3 font-teko font-bold text-md mx-auto mt-5 mb-2 px-4 text-center md:text-left md:text-lg lg:text-2xl"
          >
            {{ anime.name }}
          </h5>
          <p class="px-2 line-clamp-5 lg:line-clamp-8 lg:px-5 text-sm">
            {{ description }}
          </p>
        </div>
        <div class="absolute flex z-50 bottom-3 px-1 rounded-md">
          <AnimeCapsule
            :text="episodes.sub"
            icon="closed-captioning"
            class="bg-complementary rounded-md"
            v-if="episodes.sub"
          />
          <AnimeCapsule
            :text="episodes.dub"
            icon="microphone"
            class="bg-monochromatic-light rounded-md"
            v-if="episodes.dub"
          />
        </div>
        <img
          :src="anime.poster"
          :alt="`${anime.name} poster`"
          class="object-cover min-h-60 rounded-md lg:min-w-60 max-h-60 lg:max-w-30"
        />
      </div>
      <div>
        <h4
          class="font-teko text-md md:text-lg max-w-44 line-clamp-1 whitespace-nowrap lg:max-w-60"
        >
          {{ anime.name }}
        </h4>
      </div>
    </div>
  </NuxtLink>
  <NuxtLink
    :to="`/watch?id=${anime.id}`"
    class="group focus:outline-none hover:-translate-y-2 focus:-translate-y-2 transition duration-200 rounded-md cursor-pointer min-w-52 md:min-w-72 max-w-60 md:max-w-80"
    v-else
  >
    <div class="rounded-md">
      <div class="relative rounded-md">
        <div
          class="absolute w-full h-full z-40 rounded-md bg-bgColor opacity-0 transition duration-300 hover:opacity-100 group-focus:opacity-100 hover:bg-opacity-70 group-focus:bg-opacity-70"
        >
          <h5
            class="line-clamp-3 font-teko font-bold text-md mx-auto mt-5 mb-2 px-4 text-center md:text-left md:text-lg lg:text-2xl"
          >
            {{ anime.name }}
          </h5>
          <p class="px-2 line-clamp-5 lg:line-clamp-8 lg:px-5 text-sm">
            {{ description }}
          </p>
        </div>
        <div class="absolute flex z-50 bottom-3 px-1 rounded-md">
          <AnimeCapsule
            :text="episodes.sub"
            icon="closed-captioning"
            class="bg-complementary rounded-md"
            v-if="episodes.sub"
          />
          <AnimeCapsule
            :text="episodes.dub"
            icon="microphone"
            class="bg-monochromatic-light rounded-md"
            v-if="episodes.dub"
          />
        </div>
        <img
          :src="anime.poster"
          :alt="`${anime.name} poster`"
          class="object-cover rounded-md w-full h-72 md:h-80 lg:h-96"
        />
      </div>
      <div>
        <h4
          class="font-teko text-md md:text-xl lg:text-xl xl:text-2xl line-clamp-1 whitespace-nowrap max-w-full"
        >
          {{ anime.name }}
        </h4>
      </div>
    </div>
  </NuxtLink>
</template>
