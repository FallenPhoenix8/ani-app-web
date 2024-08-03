<script setup>
const { icon, text } = defineProps({
  icon: String | undefined,
  text: Number | String,
})
</script>
<template>
  <div
    class="ml-1 p-1 text-xs text-center text-black space-x-1 font-bold"
    :class="$attrs.class"
  >
    <span>
      <ClientOnly v-if="icon">
        <font-awesome-icon :icon="icon" />
      </ClientOnly>
    </span>
    <span>
      {{ text }}
    </span>
  </div>
</template>
