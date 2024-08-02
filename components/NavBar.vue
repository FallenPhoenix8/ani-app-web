<script setup>
const { genres } = defineProps({
  genres: Array,
})
</script>
<template>
  <nav class="z-50 flex bg-slate-800 min-w-full min-h-14 md:min-h-10">
    <NavMobileOnlyMenu />
    <NavDesktopOnlyMenu :genres="genres" />
  </nav>
</template>
