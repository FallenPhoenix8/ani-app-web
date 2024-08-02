<script setup>
const { isActive } = defineProps({
  "is-active": Boolean,
})
const emit = defineEmits(["update:is-active-menu"])
</script>
<template>
  <div
    class="absolute flex lg:hidden left-0 h-screen bg-bgColor bg-opacity-95 z-20 p-5 transition duration-200"
    :class="{ '-translate-x-full': !isActive }"
  >
    <div class="flex flex-col">
      <ClientOnly>
        <button @click="emit('update:is-active-menu')">
          <font-awesome-icon icon="x" size="lg" />
        </button>
      </ClientOnly>
    </div>
  </div>
</template>
