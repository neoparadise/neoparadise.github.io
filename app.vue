<script setup lang="ts">
import Navbar from "@/components/Navbar.vue";
import Background from "@/components/Background.vue";
import Footer from "@/components/Footer.vue";
</script>

<template>
  <Background/>
  <div class="flex flex-col min-h-screen">
    <Navbar />
    <div class="flex-grow">
      <NuxtPage />
    </div>
    <Footer />
  </div>
</template>