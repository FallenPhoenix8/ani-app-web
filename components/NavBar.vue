<script setup>
const { genres } = defineProps({
  genres: Array,
})

const isActiveMobileMenu = ref(false)

function updateIsActiveMobileMenu() {
  isActiveMobileMenu.value = !isActiveMobileMenu.value
  document.body.classList.toggle("overflow-hidden")
}
</script>
<template>
  <nav
    class="static md:sticky top-0 z-50 flex justify-between md:justify-center bg-slate-800 max-w-full min-h-14 md:min-h-10 xl:justify-around"
  >
    <NavMobileOnlyMenu
      @update:is-active-menu="() => updateIsActiveMobileMenu()"
    />
    <NavDesktopOnlyMenu :genres="genres" />
    <NavBothMenu />
    <NavMobileMenuPanel
      :is-active="isActiveMobileMenu"
      @update:is-active-menu="() => updateIsActiveMobileMenu()"
      :genres="genres"
    />
  </nav>
</template>
