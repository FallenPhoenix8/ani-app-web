<script setup>
const searchQuery = ref("")
</script>
<template>
  <div class="flex flex-row items-center">
    <form class="relative mx-5">
      <input
        type="text"
        class="border-b border-b-slate-300 bg-transparent z-20 w-52 focus:outline-none focus:w-60 lg:w-60 lg:focus:w-72 focus:border-b-primary transition-all duration-500"
        placeholder="Search anime..."
        v-model="searchQuery"
      />
      <button class="absolute right-0 z-10">
        <ClientOnly>
          <font-awesome-icon
            icon="search"
            size="xl"
            class="hover:text-primary focus:text-primary transition duration-200"
          />
        </ClientOnly>
      </button>
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
