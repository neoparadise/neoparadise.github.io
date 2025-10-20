<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { Button } from '@/components/ui/button'

const showDropdown = ref(false)
let timeoutId: ReturnType<typeof setTimeout> | null = null

function openDropdown() {
    if (timeoutId) {
        clearTimeout(timeoutId)
        timeoutId = null
    }
    showDropdown.value = true
}

function closeDropdown() {
    timeoutId = setTimeout(() => {
        showDropdown.value = false
    }, 200)
}

const isScrolled = ref(false)
const scrollProgress = ref(0)

function handleScroll() {
    const scrollY = window.scrollY
    const maxScroll = 100
    const progress = Math.min(scrollY / maxScroll, 1)
    scrollProgress.value = progress
    isScrolled.value = scrollY > 0
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
    <nav :style="{
        backgroundColor: `rgba(24, 24, 24, ${scrollProgress * 0.1})`,
        backdropFilter: `blur(${scrollProgress * 12}px)`,
        borderColor: `rgba(107, 114, 128, ${scrollProgress * 0.2})`
    }"
        :class="['flex items-center justify-between px-20 py-4 text-white relative', isScrolled ? 'sticky top-0 border-b' : '']">
        <div class="flex items-center gap-4">
            <NuxtLink to="/" class="flex items-center gap-4">
                <img src="@/assets/img/icon.png" alt="neoparadise logo" class="w-12 h-12" />
                <h1 class="text-xl font-belanosima font-bold">NEOPARADISE</h1>
            </NuxtLink>
        </div>
        <div class="hidden md:flex items-center gap-4">
            <NuxtLink to="/about_us">
                <Button class="text-white hover:bg-black/40 bg-transparent">About Us</Button>
            </NuxtLink>
            <div class="relative" @mouseenter="openDropdown" @mouseleave="closeDropdown">
                <Button class="text-white hover:bg-black/50 bg-transparent">
                    Get Involved
                    <svg class="w-4 h-4 ml-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
                    </svg>
                </Button>
                <div v-if="showDropdown"
                    class="absolute right-0 mt-2 w-48 bg-black/40 rounded-md shadow-lg z-10 overflow-hidden">
                    <NuxtLink to="/get_involved/donate" class="block px-4 py-2 text-sm text-white hover:bg-black/40">
                        Donate Funds</NuxtLink>
                    <NuxtLink to="/get_involved/volunteer" class="block px-4 py-2 text-sm text-white hover:bg-black/40">
                        Volunteer</NuxtLink>
                </div>
            </div>
            <NuxtLink to="/contact_us">
                <Button class="text-white hover:bg-black/40 bg-transparent">Contact Us</Button>
            </NuxtLink>
            <NuxtLink to="/get_involved/donate">
                <Button class="bg-primary  ml-10">Donate</Button>
            </NuxtLink>
        </div>
    </nav>
</template>