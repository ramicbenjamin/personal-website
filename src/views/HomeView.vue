<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue'
import SocialLinks from '@/components/SocialLinks.vue'
import Intro from '@/views/Intro.vue'
import avatarSrc from '@/assets/ben.png' // brand image from Intro

// Mobile menu toggle
const mobileOpen = ref(false)

// Simple nav items for in-page switching
const navItems = [
  { key: 'home', label: 'Home' },
  { key: 'about', label: 'About' },
  { key: 'experience', label: 'Experience' },
  { key: 'beyond', label: 'Beyond Engineering' }
] as const

// Current section (in-page view)
const currentView = ref<'home' | 'about' | 'experience'>('home')

// Async-loaded components for other views
const viewComponents = {
  home: Intro,
  about: defineAsyncComponent(() => import('@/views/About.vue')),
  experience: defineAsyncComponent(() => import('@/views/Experience.vue')),
  beyond: defineAsyncComponent(() => import('@/views/BeyondEngineering.vue'))
}

// Toggle view on click
function setView(key: 'home' | 'about' | 'experience') {
  currentView.value = key
  mobileOpen.value = false
}
</script>

<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 text-white">
    <!-- Header -->
    <header class="sticky top-0 z-50 bg-gradient-to-b from-gray-900/90 to-gray-900/50 backdrop-blur border-b border-white/10">
      <div class="mx-auto max-w-6xl px-4 py-4 flex items-center justify-between">
        <!-- Brand with image -->
        <button
          class="flex items-center gap-3 group"
          @click="setView('home')"
          aria-label="Go to Home"
        >
          <img
            :src="avatarSrc"
            alt="Benjamin Ramić"
            class="h-10 w-10 rounded-full object-cover ring-1 ring-teal-500/40 shadow-sm"
            loading="lazy"
            decoding="async"
          />
          <span class="text-lg font-semibold tracking-wide group-hover:text-teal-300 transition">
            Benjamin Ramić
          </span>
        </button>

        <!-- Desktop Menu -->
        <nav class="hidden md:flex items-center gap-8">
          <button
            v-for="item in navItems"
            :key="item.key"
            class="text-gray-300 hover:text-white transition"
            :class="{ 'text-teal-400': currentView === item.key }"
            @click="setView(item.key)"
          >
            {{ item.label }}
          </button>
          <a
            href="https://drive.google.com/uc?id=1oioZ9Vs6n0qzypORYAhtPSRXp9tORNQK&export=download"
            download
            class="bg-teal-400 text-black px-4 py-2 rounded-full text-sm font-medium shadow-lg hover:shadow-xl hover:bg-teal-300 transition-transform transform hover:scale-105"
          >
            Download CV
          </a>
        </nav>

        <!-- Mobile Hamburger -->
        <button
          class="md:hidden inline-flex items-center justify-center rounded-md p-2 ring-1 ring-white/10 hover:ring-white/30 transition"
          @click="mobileOpen = !mobileOpen"
          aria-label="Toggle navigation"
        >
          <svg
            v-if="!mobileOpen"
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="1.5"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5M3.75 17.25h16.5" />
          </svg>
          <svg
            v-else
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="1.5"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 -translate-y-2"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-2"
      >
        <div
          v-if="mobileOpen"
          class="md:hidden border-t border-white/10 bg-slate-900/80 backdrop-blur supports-backdrop-blur"
        >
          <nav class="mx-auto max-w-6xl px-4 py-4 flex flex-col gap-3">
            <button
              v-for="item in navItems"
              :key="item.key"
              class="px-3 py-2 rounded-md text-left text-gray-200 hover:bg-white/10 hover:text-white transition"
              :class="{ 'bg-teal-500/20 text-teal-300': currentView === item.key }"
              @click="setView(item.key)"
            >
              {{ item.label }}
            </button>
            <a
              href="https://drive.google.com/uc?id=1oioZ9Vs6n0qzypORYAhtPSRXp9tORNQK&export=download"
              download
              class="mt-2 px-3 py-2 rounded-md bg-teal-400 text-black font-medium text-sm text-center"
              @click="mobileOpen = false"
            >
              Download CV
            </a>
          </nav>
        </div>
      </transition>
    </header>

    <!-- Main (switches between Intro/About/Experience) -->
    <main class="flex-1">
      <component :is="viewComponents[currentView]" />
    </main>

    <!-- Footer -->
    <footer class="w-full border-t border-white/10">
      <!-- On mobile: centered, stacked; On md+: 3 columns, left-aligned -->
      <div
        class="mx-auto max-w-6xl px-6 py-10 grid gap-8 place-items-center text-center
               md:grid-cols-2 md:items-start md:text-left md:place-items-stretch"
      >
        <!-- Brand (small avatar + name) -->
        <div class="flex flex-col items-center md:items-start gap-3">
          <div>
            <h3 class="text-lg font-semibold text-white leading-tight">© {{ new Date().getFullYear() }} Benjamin Ramić. All rights reserved.</h3>
            <p class="mt-2 text-sm text-gray-400 max-w-sm">
              Building scalable, user-friendly software and fostering strong engineering teams.
            </p>
          </div>
        </div>

        <!-- Social -->
        <div class="w-full flex justify-center md:justify-end items-end h-full">
          <SocialLinks />
        </div>
      </div>
    </footer>
  </div>
</template>
