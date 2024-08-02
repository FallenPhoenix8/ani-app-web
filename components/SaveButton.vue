<script setup>
const isWatched = ref(false)
</script>
<template>
  <button
    class="group flex justify-center items-center text-primary h-7 w-7 p-5 border border-primary rounded-md transition duration-200 hover:shadow-lg hover:-translate-y-1 focus:shadow-lg focus:-translate-y-1 add-to-watchlist-tooltip"
    @click="isWatched = !isWatched"
    :class="{ '-translate-y-1 transition duration-200': isWatched }"
  >
    <svg
      class="min-w-5 h-5 group-hover:animate-bounce group-focus:animate-bounce"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      data-t="watchlist-svg"
      aria-labelledby="watchlist-svg"
      aria-hidden="false"
      role="img"
      fill="currentColor"
      v-if="!isWatched"
    >
      <!-- <title id="watchlist-svg">Add to Watchlist</title> -->
      <path
        d="M17 18.113l-3.256-2.326A2.989 2.989 0 0 0 12 15.228c-.629 0-1.232.194-1.744.559L7 18.113V4h10v14.113zM18 2H6a1 1 0 0 0-1 1v17.056c0 .209.065.412.187.581a.994.994 0 0 0 1.394.233l4.838-3.455a1 1 0 0 1 1.162 0l4.838 3.455A1 1 0 0 0 19 20.056V3a1 1 0 0 0-1-1z"
      ></path>
    </svg>
    <font-awesome-icon icon="bookmark" v-else class="w-5 h-5" />
  </button>
</template>
