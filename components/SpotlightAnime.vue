<script setup>
const { spotlightAnime, count } = defineProps({
  "spotlight-anime": Object,
  count: Number,
})

const indicatorArray = ref([1, 2, 3, 4, 5, 6, 7, 8, 9])

const emit = defineEmits(["change:activeSpotlight"])
</script>
<template>
  <div
    class="absolute flex flex-col justify-end items-center md:flex-row-reverse h-full w-full"
  >
    <div
      class="flex flex-col justify-center w-full md:max-w-lg md:h-full bg-gradient-to-b md:bg-gradient-to-l from-transparent to-bgColor"
    >
      <h1 class="font-teko text-center text-5xl md:text-6xl p-3">
        {{ spotlightAnime.name }}
      </h1>
      <h3
        class="flex justify-center md:justify-start items-center space-x-1 text-md text-gray-400 text-center py-3 ml-5"
      >
        <span>{{ spotlightAnime.episodes.sub }}</span>
        <span
          class="inline-block h-1 w-1 leading-none bg-gray-400 mx-[0.25rem] rotate-45"
        ></span>
        <span>Subbed</span>

        <span v-if="spotlightAnime.episodes.dub"> | </span>
        <span v-if="spotlightAnime.episodes.dub">{{
          spotlightAnime.episodes.dub
        }}</span>
        <span
          class="inline-block h-1 w-1 leading-none bg-gray-400 mx-[0.25rem] rotate-45"
          v-if="spotlightAnime.episodes.dub"
        ></span>
        <span v-if="spotlightAnime.episodes.dub">Dubbed</span>
      </h3>
      <p class="hidden md:block text-gray-300 p-5 pr-0 max-w-md">
        <span class="line-clamp-5">
          {{ spotlightAnime.description }}
        </span>
      </p>

      <ClientOnly>
        <div class="flex justify-center md:justify-start space-x-3 text-white">
          <ButtonFull
            text="Start watching E1"
            :to="`/watch?id=${spotlightAnime.id}`"
            class="ml-5"
            icon="play"
          />
          <SaveButton />
        </div>
      </ClientOnly>
      <div
        id="indicators"
        class="flex justify-center md:justify-start ml-5 mt-5 space-x-3"
      >
        <div
          class="bg-slate-500 h-2 w-6 rounded-lg indicator-tile cursor-pointer"
          v-for="indicator in indicatorArray"
          :key="indicator"
          @click="() => emit('change:activeSpotlight', indicator)"
          :class="{ 'active-indicator-tile': indicator == spotlightAnime.rank }"
        ></div>
      </div>
    </div>
  </div>
  <div class="flex justify-center">
    <img
      :src="spotlightAnime.poster"
      alt=""
      class="min-h-screen max-h-[600px] md:min-w-lg aspect-auto max-w-none"
    />
  </div>
</template>
