<script setup>
const { genres } = defineProps({
  genres: Array,
})
const isVisibleGenres = ref(false)
</script>
<template>
  <div class="hidden lg:flex space-x-10 items-center min-h-full">
    <div class="flex items-center space-x-4 min-h-full">
      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        to="/"
        @focusin="isVisibleGenres = false"
        >Home</NuxtLink
      >

      <ClientOnly>
        <NuxtLink
          class="flex relative space-x-1 p-2 rounded-t-md transition duration-200 focus:outline-primary"
          :class="{ 'bg-bgColor': isVisibleGenres }"
          to="#genres"
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
                class="mx-3 py-2 px-3 cursor-pointer transition duration-200 rounded-md hover:bg-slate-600 hover:text-primary focus:text-primary focus:outline-none focus:bg-slate-600"
                :to="{ name: 'genre', query: { genre: genre } }"
              >
                {{ genre }}
              </NuxtLink>
            </ul>
          </div>
        </NuxtLink>
      </ClientOnly>

      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        to="/#trending"
        @focusin="isVisibleGenres = false"
        >Trending</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        @focusin="isVisibleGenres = false"
        >Subbed</NuxtLink
      >
      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        @focusin="isVisibleGenres = false"
        >Dubbed</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        @focusin="isVisibleGenres = false"
        >Movies</NuxtLink
      >
      <NuxtLink
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        @focusin="isVisibleGenres = false"
        >OVAs</NuxtLink
      >
    </div>
    <div class="flex space-x-4">
      <NuxtLink
        to="/#latest-episode"
        class="hover:text-primary focus:text-primary focus:outline-none cursor-pointer"
        @focusin="isVisibleGenres = false"
        >Latest Episode</NuxtLink
      >
    </div>
  </div>
</template>
