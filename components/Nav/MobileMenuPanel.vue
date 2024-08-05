<script setup>
const { isActive, genres } = defineProps({
  "is-active": Boolean,
  genres: Array,
})
const emit = defineEmits(["update:is-active-menu"])
</script>
<template>
  <div
    class="absolute flex lg:hidden left-0 h-screen min-w-60 max-w-96 bg-bgColor bg-opacity-95 z-100 py-5 transition duration-200 overflow-y-auto no-scrollbar"
    :class="{ '-translate-x-full': !isActive }"
  >
    <div class="flex flex-col space-y-3 w-full">
      <ClientOnly>
        <div
          class="ml-5 hover:text-primary focus:text-primary focus:outline-none"
        >
          <button @click="emit('update:is-active-menu')">
            <font-awesome-icon icon="x" size="xl" />
          </button>
        </div>
        <div class="flex flex-col divide-y divide-ui-bg">
          <div class="py-3"></div>
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="/"
            @click="emit('update:is-active-menu')"
            >Home</NuxtLink
          >
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="/#trending"
            @click="emit('update:is-active-menu')"
            >Trending</NuxtLink
          >
          <div class="py-3"></div>
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="#"
            @click="emit('update:is-active-menu')"
            >Subbed Anime</NuxtLink
          >
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="#"
            @click="emit('update:is-active-menu')"
            >Dubbed Anime</NuxtLink
          >
          <div class="py-3"></div>
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="#"
            @click="emit('update:is-active-menu')"
            >Movies</NuxtLink
          >
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="#"
            @click="emit('update:is-active-menu')"
            >OVAs</NuxtLink
          >
          <div class="py-3"></div>
          <NuxtLink
            class="w-full px-4 py-2 text-xl ui-tile"
            to="/#latest-episode"
            @click="emit('update:is-active-menu')"
            >Latest Episode</NuxtLink
          >
          <div class="py-3"></div>

          <div class="grid grid-cols-2">
            <h3 class="uppercase text-gray-500 text-xs m-3">Genres</h3>
            <div></div>
            <NuxtLink
              v-for="genre in genres"
              :key="genre"
              class="mx-3 py-2 px-3 cursor-pointer transition duration-200 ui-tile text-sm"
              :to="{ name: 'genre', query: { genre: genre, page: 1 } }"
              @click="emit('update:is-active-menu')"
            >
              {{ genre }}
            </NuxtLink>
          </div>
        </div>
      </ClientOnly>
    </div>
  </div>
</template>
