<script setup lang="ts">
import { ref } from 'vue'
import avatarSrc from '@/assets/ben.png'

type ViewKey = 'home' | 'about' | 'experience' | 'beyond'

const props = defineProps<{
  currentView: ViewKey
}>()

const emit = defineEmits<{
  (e: 'select', key: ViewKey): void
}>()

const mobileOpen = ref(false)

const navItems: ReadonlyArray<{ key: ViewKey; label: string }> = [
  { key: 'home', label: 'Home' },
  { key: 'about', label: 'About' },
  { key: 'experience', label: 'Experience' },
  { key: 'beyond', label: 'Beyond Engineering' }
]

function select(key: ViewKey) {
  emit('select', key)
  mobileOpen.value = false
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <header class="fixed top-4 left-0 flex justify-center bg-transparent z-50 w-full h-[66px] lg:h-[76px]">
    <div
      class="flex items-center justify-between w-full mx-3 md:mx-20 md:px-6 max-w-[1376px]
             rounded-3xl bg-gradient-to-r from-gray-900/85 to-slate-800/70 backdrop-blur
             border border-white/10 px-6 lg:px-10 py-4 lg:py-5
             shadow-[0_8px_24px_rgba(0,0,0,0.35)]"
    >
      <button
        class="flex items-center gap-3 group"
        @click="select('home')"
        aria-label="Go to Home"
      >
        <img
          :src="avatarSrc"
          alt="Benjamin Ramić"
          class="h-8 w-8 lg:h-10 lg:w-10 rounded-full object-cover ring-1 ring-teal-500/40 shadow-sm"
        />
        <span
          class="text-base lg:text-lg font-semibold tracking-wide text-gray-200
                 group-hover:text-teal-300 transition"
        >
          Benjamin Ramić
        </span>
      </button>

      <nav class="hidden lg:flex gap-8 text-gray-300 font-medium">
        <button
          v-for="item in navItems"
          :key="item.key"
          class="hover:text-white transition-colors duration-300 font-medium text-base w-full text-nowrap"
          :class="{ 'text-teal-400': props.currentView === item.key }"
          @click="select(item.key)"
        >
          {{ item.label }}
        </button>
      </nav>

      <a
        href="https://drive.google.com/uc?id=1oioZ9Vs6n0qzypORYAhtPSRXp9tORNQK&export=download"
        download
      >
        <button
          class="hidden lg:block bg-teal-400 hover:bg-teal-300 text-black font-semibold
                 rounded-full px-5 py-2 text-sm shadow-lg hover:shadow-xl
                 transition-transform transform hover:scale-105"
        >
          Download CV →
        </button>
      </a>

      <div class="lg:hidden">
        <button
          class="text-white focus:outline-none flex justify-center items-center rounded-md p-2
                 ring-1 ring-white/10 hover:ring-white/30 transition"
          @click="mobileOpen = !mobileOpen"
          aria-label="Toggle navigation"
        >
          <svg
            v-if="!mobileOpen"
            xmlns="http://www.w3.org/2000/svg"
            width="20" height="20" viewBox="0 0 24 24"
            fill="none" stroke="currentColor" stroke-width="2"
            stroke-linecap="round" stroke-linejoin="round"
          >
            <path d="M4 12h16" />
            <path d="M4 18h16" />
            <path d="M4 6h16" />
          </svg>
          <svg
            v-else
            xmlns="http://www.w3.org/2000/svg"
            width="20" height="20" viewBox="0 0 24 24"
            fill="none" stroke="currentColor" stroke-width="2"
            stroke-linecap="round" stroke-linejoin="round"
          >
            <path d="M6 18L18 6" />
            <path d="M6 6l12 12" />
          </svg>
        </button>
      </div>
    </div>

    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div v-if="mobileOpen" class="absolute top-full w-full flex justify-center pt-3 px-3">
        <div
          class="w-full max-w-[1376px] mx-auto rounded-3xl bg-gradient-to-r
                 from-gray-900/95 to-slate-800/85 backdrop-blur border border-white/10
                 shadow-[0_12px_32px_rgba(0,0,0,0.45)]"
        >
          <nav class="px-4 py-5 flex flex-col gap-3">
            <button
              v-for="item in navItems"
              :key="item.key"
              class="px-3 py-3 rounded-2xl text-left text-gray-200 hover:bg-white/10
                     hover:text-white transition"
              :class="{ 'bg-white/10 text-teal-300 ring-1 ring-white/10': props.currentView === item.key }"
              @click="select(item.key)"
            >
              {{ item.label }}
            </button>
            <a
              href='https://drive.google.com/uc?id=1oioZ9Vs6n0qzypORYAhtPSRXp9tORNQK&export=download'
              download
              class="mt-2 px-3 py-3 rounded-2xl bg-teal-400 text-black font-medium
                     text-sm text-center hover:bg-teal-300 transition"
              @click="mobileOpen = false"
            >
              Download CV
            </a>
          </nav>
        </div>
      </div>
    </transition>
  </header>
</template>
