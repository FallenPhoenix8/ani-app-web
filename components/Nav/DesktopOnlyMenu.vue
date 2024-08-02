<script setup>
const { genres } = defineProps({
  genres: Array,
})
const isVisibleGenres = ref(false)
console.log(genres)
</script>
<template>
  <div class="hidden md:flex space-x-10 items-center min-h-full">
    <div class="flex items-center space-x-4 min-h-full">
      <NuxtLink class="hover:text-primary cursor-pointer">Home</NuxtLink>

      <ClientOnly>
        <div
          class="flex relative space-x-1 p-2 transition duration-200"
          :class="{ 'bg-bgColor': isVisibleGenres }"
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
            class="absolute top-full important-left-0 rounded-b-md z-30 bg-bgColor"
            :class="{ hidden: !isVisibleGenres }"
          >
            <h3 class="uppercase text-gray-500 text-xs m-3">Genres</h3>
            <ul class="grid grid-cols-5 max-w-none min-w-max pb-4">
              <li
                v-for="genre in genres"
                :key="genre"
                class="mx-3 py-2 px-3 cursor-pointer transition duration-200 rounded-md hover:bg-slate-600 hover:text-primary"
              >
                <NuxtLink :to="{ name: 'genre', query: { genre: genre } }">
                  {{ genre }}
                </NuxtLink>
              </li>
            </ul>
          </div>
        </div>
      </ClientOnly>

      <NuxtLink class="hover:text-primary cursor-pointer"
        >Most Popular</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink class="hover:text-primary cursor-pointer"
        >Subbed Anime</NuxtLink
      >
      <NuxtLink class="hover:text-primary cursor-pointer"
        >Dubbed Anime</NuxtLink
      >
    </div>

    <div class="flex space-x-4">
      <NuxtLink class="hover:text-primary cursor-pointer">Movies</NuxtLink>
      <NuxtLink class="hover:text-primary cursor-pointer">OVAs</NuxtLink>
    </div>
  </div>
</template>
