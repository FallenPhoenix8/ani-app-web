<script setup>
const { animes, title, isUpcoming } = defineProps({
  animes: Array,
  title: String,
  "is-upcoming": Boolean | null,
})

const rowElement = ref(null)
const isVisibleEndButton = ref(true)
const previousScrollLeft = ref(0)

const scrollToEnd = () => {
  rowElement.value.scrollTo({
    left: rowElement.value.scrollWidth,
    behavior: "smooth",
  })
  isVisibleEndButton.value = false
}

function handleScroll(event) {
  const { scrollLeft } = event.target
  if (scrollLeft < previousScrollLeft.value) {
    isVisibleEndButton.value = true
  }
  previousScrollLeft.value = scrollLeft
}
</script>
<template>
  <div :id="$attrs.id" class="flex flex-col">
    <h2 class="max-w-md">{{ title }}</h2>
    <div
      class="relative flex mb-5 space-x-10 lg:space-x-7 overflow-x-auto max-w-none no-scrollbar"
      ref="rowElement"
      @scroll="(event) => handleScroll(event)"
    >
      <AnimeCard
        v-for="anime in animes"
        :anime="anime"
        :key="anime"
        :is-upcoming="isUpcoming"
      />

      <button
        class="sticky flex flex-col justify-center items-center right-0 top-0 bottom-0 min-h-full px-4 rounded-md bg-ui-bg bg-opacity-50 z-10"
        :class="{ hidden: !isVisibleEndButton }"
        role="button"
        tabindex="0"
        @click.prevent="scrollToEnd"
      >
        <ClientOnly>
          <font-awesome-icon icon="angle-right" />
        </ClientOnly>
      </button>
    </div>
  </div>
</template>
