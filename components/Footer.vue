<template>
  <footer class="bg-background/30 text-white py-8 mt-10">
    <div class="container mx-auto px-4 text-center">
      <div class="flex flex-col md:flex-row justify-between items-center mb-4">
        <div class="mb-4 md:mb-0 flex items-center gap-2">
          <img src="@/assets/img/icon.png" alt="NeoParadise logo" class="w-16 h-16" />
          <NuxtLink to="/" class="text-xl font-bold font-belanosima">NeoParadise</NuxtLink>
        </div>
        <nav class="flex space-x-4">
          <NuxtLink to="/" class="hover:text-gray-400">Privacy Policy</NuxtLink>
          <NuxtLink to="/" class="hover:text-gray-400">Terms of Service</NuxtLink>
          <NuxtLink to="/" class="hover:text-gray-400">Sitemap</NuxtLink>
        </nav>
        <div class="flex space-x-4 mt-4 md:mt-0">
          <a href="#" class="hover:text-gray-400">Facebook</a>
          <a href="#" class="hover:text-gray-400">Twitter</a>
          <a href="#" class="hover:text-gray-400">Instagram</a>
        </div>
      </div>
      <p class="text-sm text-gray-500">&copy; {{ new Date().getFullYear() }} NeoParadise. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup lang="ts">
// No script logic needed for a basic footer
</script>

<style scoped>
/* Add any component-specific styles here if needed */
</style>
