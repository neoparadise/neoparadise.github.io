<script setup lang="ts">
// No Card components used
</script>

<template>
  <div class="flex flex-col justify-center items-center min-h-[calc(100vh-var(--navbar-height))] p-4 text-center">
    <h1 class="text-destructive text-3xl font-bold mb-4">Donation Cancelled</h1>
    <p class="text-lg mb-4 max-w-2xl">
      Your donation process was cancelled. If you encountered any issues or changed your mind, you can return to the
      <NuxtLink to="/get_involved/donate" class="text-secondary hover:underline">donation page</NuxtLink>.
    </p>
  </div>
</template>
