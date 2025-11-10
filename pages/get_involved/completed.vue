<script setup lang="ts">
// No Card components used
</script>

<template>
  <div class="flex flex-col justify-center items-center min-h-[calc(100vh-var(--navbar-height))] p-4 text-center">
    <h1 class="text-primary text-3xl font-bold mb-4">Donation Completed Successfully!</h1>
    <p class="text-lg mb-4  max-w-2xl">
      Thank you for your generous donation. Your support is greatly appreciated and helps us continue our work.
    </p>
    <p class="text-lg">
      You can return to the <NuxtLink to="/" class="text-secondary hover:underline">homepage</NuxtLink> or explore other ways to <NuxtLink to="/get_involved/volunteer" class="text-secondary hover:underline">get involved</NuxtLink>.
    </p>
  </div>
</template>
