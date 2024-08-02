<script setup>
const { text } = defineProps({
  text: String,
})
const isMouseIn = ref(true)
</script>
<template>
  <a
    :href="$attrs.href"
    :class="$attrs.class"
    class="group px-5 py-2 bg-primary text-black uppercase text-center max-w-60 rounded-md shadow transition duration-200 hover:shadow-lg hover:-translate-y-1 focus:shadow-lg focus:-translate-y-1"
    @mouseenter="isMouseIn = !isMouseIn"
    @mouseleave="isMouseIn = !isMouseIn"
    @focusin="isMouseIn = !isMouseIn"
    @focusout="isMouseIn = !isMouseIn"
  >
    <span class="flex items-center">
      <img
        src="~/assets/images/icons/play.svg"
        alt=""
        class="h-5 w-5"
        v-if="isMouseIn"
      />
      <font-awesome-icon icon="play" beat-fade v-else />

      <span class="ml-3 transition duration-200 group-focus:-translate-x-1">{{
        text
      }}</span>
    </span>
  </a>
</template>
