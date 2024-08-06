<script setup>
import SearchSuggestionCard from "./SearchSuggestionCard.vue"

const { suggestions, searchQuery } = defineProps({
  suggestions: Object,
  searchQuery: String,
})
</script>
<template>
  <div
    class="fixed flex flex-col justify-center w-full top-16 left-0 right-0 z-100 py-4"
    :class="{ 'bg-slate-800': searchQuery.length > 0 }"
  >
    <h3
      class="uppercase text-gray-500 text-xs m-3"
      v-if="searchQuery.length > 0"
    >
      Suggestions
    </h3>
    <div class="flex flex-col space-y-4 divide-y divide-ui-bg">
      <SearchSuggestionCard
        v-for="anime in suggestions.suggestions"
        :key="`${anime}-suggestion`"
        :anime="anime"
        v-if="searchQuery"
      />
    </div>
  </div>
</template>
