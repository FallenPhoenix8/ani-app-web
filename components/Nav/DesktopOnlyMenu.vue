<script setup>
const { genres } = defineProps({
  genres: Array,
})
const isVisibleGenres = ref(false)
</script>
<template>
  <div
    class="hidden lg:flex items-center min-h-full text-sm xl:space-x-10 xl:text-base"
  >
    <div class="flex items-center space-x-4 min-h-full">
      <NuxtLink
        class="ui-tile px-3 py-2"
        to="/"
        @focusin="isVisibleGenres = false"
        >Home</NuxtLink
      >

      <ClientOnly>
        <NuxtLink
          class="flex relative space-x-1 p-2 rounded-t-md transition duration-200 ui-tile"
          :class="{ 'bg-bgColor': isVisibleGenres }"
          to="#"
          @click="isVisibleGenres = !isVisibleGenres"
        >
          <span class="cursor-pointer">Genres</span>
          <div
            class="transition duration-200 cursor-pointer"
            :class="{ 'rotate-90': isVisibleGenres }"
          >
            <font-awesome-icon icon="angle-right" />
          </div>
          <div
            id="genres"
            class="absolute top-full important-left-0 rounded-b-md z-30 bg-bgColor text-white"
            :class="{ hidden: !isVisibleGenres }"
          >
            <h3 class="uppercase text-gray-500 text-xs m-3">Genres</h3>
            <ul class="grid grid-cols-5 max-w-none min-w-max pb-4">
              <NuxtLink
                v-for="genre in genres"
                :key="genre"
                class="mx-3 py-2 px-3 cursor-pointer ui-tile"
                :to="{ name: 'genre', query: { genre: genre, page: 1 } }"
              >
                {{ genre }}
              </NuxtLink>
            </ul>
          </div>
        </NuxtLink>
      </ClientOnly>

      <NuxtLink
        class="ui-tile px-3 py-2 h-full"
        to="/#trending"
        @focusin="isVisibleGenres = false"
        >Trending</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink
        class="ui-tile px-3 py-2 h-full"
        @focusin="isVisibleGenres = false"
        to="/subbed-anime?page=1"
        >Subbed</NuxtLink
      >
      <NuxtLink
        class="ui-tile px-3 py-2 h-full"
        @focusin="isVisibleGenres = false"
        to="/dubbed-anime?page=1"
        >Dubbed</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink
        class="ui-tile px-3 py-2 h-full"
        @focusin="isVisibleGenres = false"
        to="/movie?page=1"
        >Movies</NuxtLink
      >
      <NuxtLink
        class="ui-tile px-3 py-2 h-full"
        @focusin="isVisibleGenres = false"
        to="/ova?page=1"
        >OVAs</NuxtLink
      >
    </div>
    <div class="flex space-x-4">
      <NuxtLink
        to="/#latest-episode"
        class="ui-tile px-3 py-2 h-full"
        @focusin="isVisibleGenres = false"
        >Latest Episode</NuxtLink
      >
    </div>
  </div>
</template>
