<script setup lang="ts">
import { Button } from '@/components/ui/button'
</script>

<template>
  <div class="p-5 text-center">
    <h1 class="mb-2 text-3xl font-bold">Donate to Our Cause</h1>
    <p class="mb-5 text-lg">Your support helps us continue our mission. Please click the button below to make a secure donation via PayPal.</p>
    <Button as-child class="mt-4 px-8 py-4 text-lg">
      <a href="https://www.paypal.com/donate/?hosted_button_id=YGK8C5VEEBVA2" target="_blank" rel="noopener noreferrer">
        Donate with PayPal
      </a>
    </Button>
    <p class="mt-5 text-sm text-gray-600">You will be redirected to PayPal's secure website to complete your donation.</p>
  </div>
</template>
