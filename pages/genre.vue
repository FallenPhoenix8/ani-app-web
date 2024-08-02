<script setup>
const genre = useRoute().query.genre
</script>
<template>
  <div>{{ genre }}</div>
</template>
