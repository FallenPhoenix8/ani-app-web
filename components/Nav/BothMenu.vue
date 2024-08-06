<script setup>
const searchQuery = ref("")
const suggestions = ref([])
const loading = ref(true)

watch(
  () => searchQuery.value,
  async () => {
    loading.value = true
    if (searchQuery.value) {
      await fetch(
        `http://193.150.21.20:3004/anime/search/suggest?q=${searchQuery.value}`
      )
        .then((res) => res.json())
        .then((data) => {
          suggestions.value = data
          loading.value = false
        })
        .catch((err) => console.error(err))
    } else {
      suggestions.value = []
    }
  }
)
</script>
<template>
  <div class="flex flex-row items-center">
    <form class="mx-5 py-5">
      <input
        type="text"
        class="border-b border-b-slate-300 bg-transparent z-20 w-52 focus:outline-none focus:w-60 lg:w-60 lg:focus:w-72 focus:border-b-primary transition-all duration-500"
        placeholder="Search anime..."
        v-model="searchQuery"
      />
      <button class="z-10 -ml-6">
        <ClientOnly>
          <font-awesome-icon
            icon="search"
            size="xl"
            class="hover:text-primary focus:text-primary transition duration-200"
          />
        </ClientOnly>
      </button>
      <AnimeSuggestionsContainer
        :search-query="searchQuery"
        :suggestions="suggestions"
        v-if="!loading"
      />
    </form>

    <!-- TODO PFP SYSTEM -->
    <NuxtLink class="py-2" to="#">
      <img
        src="https://picsum.photos/100"
        alt=""
        class="aspect-square rounded-full max-h-12"
      />
    </NuxtLink>
  </div>
</template>
