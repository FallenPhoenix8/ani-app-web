<script setup>
const { text, icon } = defineProps({
  text: String,
  icon: String,
})

const isMouseIn = ref(true)
const iconPath = `/images/icons/${icon}.svg`
</script>
<template>
  <NuxtLink
    :to="$attrs.to"
    :class="$attrs.class"
    class="group px-5 py-2 bg-primary text-black uppercase text-center max-w-60 rounded-md shadow transition duration-200 hover:shadow-lg hover:-translate-y-1 focus:shadow-lg focus:-translate-y-1"
    @mouseenter="isMouseIn = !isMouseIn"
    @mouseleave="isMouseIn = !isMouseIn"
    @focusin="isMouseIn = !isMouseIn"
    @focusout="isMouseIn = !isMouseIn"
  >
    <span class="flex items-center">
      <img :src="iconPath" alt="" class="h-5 w-5" v-if="isMouseIn" />
      <font-awesome-icon :icon="icon" beat-fade v-else />

      <span class="ml-3 transition duration-200 group-focus:-translate-x-1">{{
        text
      }}</span>
    </span>
  </NuxtLink>
</template>
