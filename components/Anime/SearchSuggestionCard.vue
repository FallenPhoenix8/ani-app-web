<script setup>
const { anime } = defineProps({
  anime: Object,
})
</script>
<template>
  <NuxtLink :to="`/watch?id=${anime.id}`" class="flex space-x-3 pt-3">
    <img :src="anime.poster" :alt="anime.name" class="object-contain w-20" />
    <div class="flex flex-col justify-between">
      <div>
        <h3 class="font-mina text-lg">{{ anime.name }}</h3>
        <h5 class="font-mina text-sm font-thin">{{ anime.jname }}</h5>
      </div>

      <div class="flex">
        <span
          v-for="(info, index) in anime.moreInfo"
          class="text-xs font-thin font-mina"
        >
          <h6 class="inline-block">{{ info }}</h6>
          <span
            class="inline-block h-1 w-1 leading-none bg-gray-400 mx-[0.25rem] rotate-45 my-0.5"
            v-if="index < anime.moreInfo.length - 1"
          ></span>
        </span>
      </div>
    </div>
  </NuxtLink>
</template>
