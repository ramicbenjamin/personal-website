<script setup lang="ts">
import { ref } from 'vue'

const isClicked = ref(false)

function handleClick() {
  isClicked.value = !isClicked.value
}

function closeCallout() {
  isClicked.value = false
}
</script>

<template>
  <section
    class="w-full flex flex-col items-center justify-center px-6 py-16 text-center"
    style="min-height: calc(100svh - var(--header-h, 64px) - var(--footer-h, 180px))"
  >
    <div class="relative flex w-full items-center justify-center py-4 md:h-56">
      <div class="flex flex-col items-center gap-4 md:flex-row md:gap-5">
        <button
          type="button"
          class="relative h-48 w-48 shrink-0 rounded-full transition-transform duration-500 ease-out focus:outline-none focus-visible:ring-2 focus-visible:ring-teal-300"
          :class="isClicked ? 'md:-translate-x-3' : 'hover:scale-105'"
          @click="handleClick"
          aria-label="Toggle contact callout"
        >
          <img
            src="@/assets/ben.png"
            alt="Benjamin Ramić"
            class="h-full w-full rounded-full object-cover shadow-[0_10px_35px_rgba(20,184,166,0.35)] ring-2 ring-teal-400/45"
            loading="lazy"
            decoding="async"
          />

          <!-- Always visible availability indicator -->
          <span class="absolute top-1 right-6 flex h-5 w-5 items-center justify-center">
            <span
              class="absolute inline-flex h-full w-full rounded-full border-2 border-emerald-400/80 animate-ping"
            ></span>
            <span
              class="relative inline-flex h-5 w-5 rounded-full border-2 border-slate-900 bg-emerald-500 shadow-[0_0_0_4px_rgba(34,197,94,0.42)]"
              :class="isClicked ? 'shadow-[0_0_0_5px_rgba(34,197,94,0.58)]' : ''"
            ></span>
          </span>
        </button>

        <div
          class="overflow-hidden transition-all duration-500 ease-out md:shrink-0"
          :class="
            isClicked
              ? 'max-h-[26rem] opacity-100 md:w-80 md:max-h-48 md:translate-x-0'
              : 'max-h-0 opacity-0 pointer-events-none md:w-0 md:max-h-48 md:-translate-x-2'
          "
        >
          <div
            class="relative mx-auto flex w-full max-w-sm flex-col items-center justify-center gap-2.5 rounded-2xl border border-teal-400/35 bg-slate-900/35 px-4 py-4 text-center backdrop-blur-md md:h-48 md:w-80 md:max-w-none md:px-5"
          >
            <button
              type="button"
              class="absolute right-2 top-2 inline-flex h-7 w-7 items-center justify-center rounded-full bg-white/10 text-gray-200 transition-colors hover:bg-white/20 hover:text-white focus:outline-none focus-visible:ring-2 focus-visible:ring-teal-300"
              @click="closeCallout"
              aria-label="Close contact callout"
            >
              <svg class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path
                  fill-rule="evenodd"
                  d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>

            <div class="inline-flex w-fit items-center gap-2 rounded-full border border-teal-400/45 bg-teal-500/15 px-3 py-1 text-xs font-semibold text-teal-300">
              <span class="h-2.5 w-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
              Open to Chat
            </div>

            <h3 class="text-base font-bold leading-tight text-white md:text-lg">Let's Connect!</h3>

            <p class="max-w-[18rem] text-[11px] leading-relaxed text-gray-300 md:text-xs md:leading-snug">
              I enjoy connecting with fellow engineers and discussing technology, software
              architecture, and team dynamics.
            </p>

            <a
              href="https://www.linkedin.com/in/ramicbenjamin/"
              target="_blank"
              rel="noopener noreferrer"
              class="inline-flex w-fit items-center gap-1.5 whitespace-nowrap rounded-lg bg-[#0A66C2] px-3 py-1.5 text-xs font-semibold text-white shadow-lg transition-colors duration-300 hover:bg-[#004182] hover:shadow-xl"
            >
              <svg class="h-4 w-4" fill="currentColor" viewBox="0 0 24 24">
                <path
                  d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                />
              </svg>
              Message on LinkedIn
            </a>
          </div>
        </div>
      </div>
    </div>

    <h1 class="text-4xl md:text-6xl font-extrabold tracking-wide mt-6">
      Hi, I'm <span class="text-teal-400">Benjamin Ramić</span>
    </h1>

    <p class="text-lg md:text-xl text-gray-300 mt-4 max-w-2xl">
      I'm a passionate <span class="text-blue-400 font-bold">Software Engineer</span> with a proven
      track record of building scalable, efficient, and user-friendly software solutions. Over the
      years, I've developed a strong ability to work with teams and lead them toward achieving
      technical and business goals.
    </p>

    <p class="text-lg md:text-xl text-gray-300 mt-4 max-w-2xl">
      I thrive in collaborative environments where innovation meets execution. I'm skilled at
      fostering growth within teams, mentoring developers, and designing processes that drive
      success.
    </p>
  </section>
</template>

