<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue'
import SocialLinks from '@/components/SocialLinks.vue'
import Intro from '@/views/Intro.vue'
import HeaderNav from '@/components/HeaderNav.vue'

const currentView = ref<'home' | 'about' | 'experience' | 'beyond'>('home')

const viewComponents = {
  home: Intro,
  about: defineAsyncComponent(() => import('@/views/About.vue')),
  experience: defineAsyncComponent(() => import('@/views/Experience.vue')),
  beyond: defineAsyncComponent(() => import('@/views/BeyondEngineering.vue'))
}

function handleSelect(key: 'home' | 'about' | 'experience' | 'beyond') {
  currentView.value = key
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 text-white">
    <HeaderNav :current-view="currentView" @select="handleSelect" />

    <div aria-hidden="true" class="pt-[140px] md:pt-[90px] lg:pt-[100px]"></div>

    <main class="flex-1">
      <component :is="viewComponents[currentView]" />
    </main>

    <footer class="w-full border-t border-white/10">
      <div class="mx-auto max-w-6xl px-6 py-10 grid gap-8 place-items-center text-center md:grid-cols-2 md:items-start md:text-left md:place-items-stretch">
        <div class="flex flex-col items-center md:items-start gap-3">
          <div>
            <h3 class="text-lg font-semibold text-white leading-tight">© {{ new Date().getFullYear() }} Benjamin Ramić. All rights reserved.</h3>
            <p class="mt-2 text-sm text-gray-400 max-w-sm">
              Building scalable, user-friendly software and fostering strong engineering teams.
            </p>
          </div>
        </div>

        <div class="w-full flex justify-center md:justify-end items-end h-full">
          <SocialLinks />
        </div>
      </div>
    </footer>
  </div>
</template>
