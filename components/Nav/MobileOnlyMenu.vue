<script setup>
const emit = defineEmits(["update:is-active-menu"])
</script>
<template>
  <button class="ml-5 md:hidden" @click="() => emit('update:is-active-menu')">
    <div>
      <ClientOnly>
        <font-awesome-icon icon="bars" size="xl" />
      </ClientOnly>
    </div>
  </button>
  <div class="ml-5 min-w-[21px] hidden md:inline-block"></div>
</template>
