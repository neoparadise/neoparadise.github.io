<script setup lang="ts">
import { Input } from '@/components/ui/input'
import { Textarea } from '@/components/ui/textarea'
import { Button } from '@/components/ui/button'
</script>

<template>
  <div class="container py-10 max-w-4xl mx-auto px-4">
    <h1 class="text-3xl font-bold mb-4">Contact Us</h1>
    <p class="text-gray-600 mb-8">We'd love to hear from you! Please fill out the form below.</p>
    <form action="https://formsubmit.co/willmeyburgh@gmail.com" method="POST" class="space-y-4">
      <input type="hidden" name="_subject" value="New Contact Form Submission">
      <input type="hidden" name="_next" value="https://neoparadise.github.io/thanks">
      <div>
        <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
        <Input id="name" name="name" type="text" placeholder="Your Name" required />
      </div>
      <div>
        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
        <Input id="email" name="email" type="email" placeholder="your@email.com" required />
      </div>
      <div>
        <label for="message" class="block text-sm font-medium text-gray-700">Message</label>
        <Textarea id="message" name="message" placeholder="Your message..." class="h-32" required />
      </div>
      <Button type="submit" class="w-full">Send Message</Button>
    </form>
  </div>
</template>

<style scoped>
/* Add any component-specific styles here if needed */
</style>