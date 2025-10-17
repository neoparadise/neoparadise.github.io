<template>
  <div class="flex items-center justify-center h-screen bg-gray-100">
    <Card class="w-[350px]">
      <CardHeader>
        <CardTitle>NeoParadise</CardTitle>
        <CardDescription>Your next-generation platform is coming soon!</CardDescription>
      </CardHeader>
      <CardContent>
        <p class="text-center text-gray-600">We're working hard to bring you an amazing experience. Stay tuned for updates!</p>
      </CardContent>
      <CardFooter class="flex justify-center">
        <Button>Get Notified</Button>
      </CardFooter>
    </Card>
  </div>
</template>

<script setup lang="ts">
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
</script>
