<script setup>
const { anime } = defineProps({
  anime: Object,
})
const description = ref("")
onMounted(async () => {
  await fetch(`http://luka.lafp.cc:3004/anime/info?id=${anime.id}`)
    .then((res) => res.json())
    .then((data) => {
      description.value = data.anime.info.description
      console.log(description)
    })
    .catch((err) => console.error(err))
})
</script>
<template>
  <NuxtLink
    to="#"
    class="group focus:outline-none focus:-translate-y-2 transition duration-200 rounded-md"
  >
    <div class="rounded-md">
      <div class="relative min-h-52 rounded-md min-w-40">
        <div
          class="absolute w-full h-full z-50 rounded-md bg-bgColor opacity-0 transition duration-200 hover:opacity-70 group-focus:opacity-70"
        >
          <p class="p-5 line-clamp-6">
            {{ description }}
          </p>
        </div>
        <img
          :src="anime.poster"
          :alt="`${anime.name} poster`"
          class="object-cover h-60 rounded-md"
        />
      </div>
      <div>
        <h4 class="font-teko text-xl md:text-2xl max-w-44">{{ anime.name }}</h4>
      </div>
    </div>
  </NuxtLink>
</template>
