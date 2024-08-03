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
    class="static md:sticky top-0 z-50 flex justify-between bg-slate-800 min-w-full min-h-14 md:min-h-10 lg:justify-around"
  >
    <NavMobileOnlyMenu
      @update:is-active-menu="() => updateIsActiveMobileMenu()"
    />
    <NavDesktopOnlyMenu :genres="genres" />
    <NavBothMenu />
    <NavMobileMenuPanel
      :is-active="isActiveMobileMenu"
      @update:is-active-menu="() => updateIsActiveMobileMenu()"
    />
  </nav>
</template>
