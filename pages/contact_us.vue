<script setup lang="ts">
import { ref } from 'vue'
import { Input } from '@/components/ui/input'
import { Textarea } from '@/components/ui/textarea'
import { Button } from '@/components/ui/button'

const name = ref('')
const email = ref('')
const message = ref('')

function handleSubmit() {
  console.log('Form submitted:', { name: name.value, email: email.value, message: message.value })
  alert('Thank you for your message! We will get back to you soon.')
  // Here you would typically send the data to an API
  name.value = ''
  email.value = ''
  message.value = ''
}
</script>

<template>
  <div class="container py-10 max-w-4xl mx-auto px-4">
    <h1 class="text-3xl font-bold mb-4">Contact Us</h1>
    <p class="text-gray-600 mb-8">We'd love to hear from you! Please fill out the form below.</p>
    <form @submit.prevent="handleSubmit" class="space-y-4">
      <div>
        <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
        <Input id="name" v-model="name" type="text" placeholder="Your Name" required />
      </div>
      <div>
        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
        <Input id="email" v-model="email" type="email" placeholder="your@email.com" required />
      </div>
      <div>
        <label for="message" class="block text-sm font-medium text-gray-700">Message</label>
                    <Textarea id="message" v-model="message" placeholder="Your message..." class="h-32" required />      </div>
      <Button type="submit" class="w-full">Send Message</Button>
    </form>
  </div>
</template>

<style scoped>
/* Add any component-specific styles here if needed */
</style>