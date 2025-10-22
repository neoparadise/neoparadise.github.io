<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { Button } from '@/components/ui/button'

const showDropdown = ref(false)
const showMobileMenu = ref(false) // New reactive variable for mobile menu
const isScrollingToTop = ref(false) // New reactive variable to track scroll-to-top
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

    // Close mobile menu if scrolled while open and not actively scrolling to top
    if (showMobileMenu.value && scrollY > 0 && !isScrollingToTop.value) {
        showMobileMenu.value = false
    }
}

function monitorScrollToTop() {
    if (window.scrollY === 0) {
        isScrollingToTop.value = false
        showMobileMenu.value = true // Open the menu after scroll
    } else {
        requestAnimationFrame(monitorScrollToTop)
    }
}

function toggleMobileMenu() {
    if (isScrolled.value && !showMobileMenu.value) {
        isScrollingToTop.value = true
        window.scrollTo({ top: 0, behavior: 'smooth' })
        requestAnimationFrame(monitorScrollToTop)
    } else {
        showMobileMenu.value = !showMobileMenu.value
    }
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
        :class="['flex flex-col py-4 text-white relative', isScrolled ? 'sticky top-0 border-b' : '']">
        <div class="flex items-center justify-between w-full">
            <div class="flex items-center gap-4">
                <NuxtLink to="/" class="flex items-center gap-2 pl-4">
                    <img src="@/assets/img/icon.png" alt="neoparadise logo" class="w-12 h-12" />
                    <h1 class="text-xl font-belanosima font-bold lg:block">NEOPARADISE</h1>
                </NuxtLink>
            </div>

            <!-- Desktop Navigation -->
            <div class="lg:flex hidden items-center gap-4 pr-4">
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
                    <Button class="bg-primary ml-10">Donate</Button>
                </NuxtLink>
            </div>

            <!-- Mobile Navigation -->
            <div class="lg:hidden flex items-center gap-4 pr-4">
                <NuxtLink to="/get_involved/donate">
                    <Button class="bg-primary">Donate</Button>
                </NuxtLink>
                <Button @click="toggleMobileMenu" class="text-white  bg-transparent p-2">
                    <svg v-if="!showMobileMenu" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
                    </svg>
                    <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </Button>
            </div>
        </div>

        <!-- Mobile Menu Dropdown -->
        <div v-if="showMobileMenu"
            :style="{ borderColor: `rgba(107, 114, 128, 0.2)` }"
            class="lg:hidden w-full bg-transparent z-20 py-2 border-b">
            <div class="px-4">
                <NuxtLink to="/about_us" class="block py-2 text-sm text-white" @click="showMobileMenu = false">About Us</NuxtLink>
                <div class="relative">
                    <div @click="showDropdown = !showDropdown" class="w-full text-left justify-start text-white bg-transparent py-2 text-sm">
                        Get Involved
                        <svg v-if="showDropdown" class="w-4 h-4 inline-block" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7"></path>
                        </svg>
                        <svg v-else class="w-4 h-4 inline-block" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
                        </svg>
                    </div>
                    <div v-if="showDropdown">
                        <NuxtLink to="/get_involved/donate" class="block ml-2 py-2 text-sm text-white " @click="showMobileMenu = false">Donate Funds</NuxtLink>
                        <NuxtLink to="/get_involved/volunteer" class="block  ml-2 py-2 text-sm text-white 0" @click="showMobileMenu = false">Volunteer</NuxtLink>
                    </div>
                </div>
                <NuxtLink to="/contact_us" class="block py-2 text-sm text-white " @click="showMobileMenu = false">Contact Us</NuxtLink>
            </div>
        </div>
    </nav>
</template>