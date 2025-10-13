<script setup lang="ts">
import { ref } from 'vue'

const flipped = ref(false)
function toggle() { flipped.value = !flipped.value }
function setFlip(v: boolean) { flipped.value = v }
</script>

<template>
  <section
    class="w-full flex flex-col items-center justify-center px-6 py-16 text-center"
    style="min-height: calc(100svh - var(--header-h, 64px) - var(--footer-h, 180px));"
  >
    <!-- Coin Flip Avatar -->
    <div
      class="relative w-48 h-48 cursor-pointer perspective-1000"
      @mouseenter="setFlip(true)"
      @mouseleave="setFlip(false)"
      @click="toggle"
      aria-label="Profile coin flip"
      role="img"
    >
      <div class="flip-inner" :class="{ 'is-flipped': flipped }">
        <!-- FRONT -->
        <div class="flip-face flip-front rounded-full overflow-hidden shadow-lg">
          <img
            src="@/assets/ben.png"
            alt="Benjamin Ramić"
            class="w-full h-full object-cover"
            loading="lazy"
            decoding="async"
          />
        </div>

        <!-- BACK -->
        <div
          class="flip-face flip-back rounded-full overflow-hidden shadow-lg bg-gradient-to-b from-teal-700/90 to-slate-900/90 text-white flex flex-col items-center justify-center px-4"
        >
          <div class="text-3xl mb-1">👋</div>
          <div class="text-base sm:text-lg font-semibold leading-snug">
            Let’s work together!
          </div>
        </div>
      </div>
    </div>

    <!-- Title -->
    <h1 class="text-4xl md:text-6xl font-extrabold tracking-wide mt-6">
      Hi, I’m <span class="text-teal-400">Benjamin Ramić</span>
    </h1>

    <p class="text-lg md:text-xl text-gray-300 mt-4 max-w-2xl">
      I’m a passionate <span class="text-blue-400 font-bold">Software Engineer</span> with a proven track record of
      building scalable, efficient, and user-friendly software solutions. Over the years, I’ve developed a strong ability
      to work with teams and lead them toward achieving technical and business goals.
    </p>

    <p class="text-lg md:text-xl text-gray-300 mt-4 max-w-2xl">
      I thrive in collaborative environments where innovation meets execution. I’m skilled at fostering growth within
      teams, mentoring developers, and designing processes that drive success.
    </p>
  </section>
</template>

<style scoped>
.perspective-1000 { perspective: 1000px; }
.flip-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform .7s ease;
}
.flip-inner.is-flipped { transform: rotateY(180deg) scale(1.03); }

/* Faces */
.flip-face {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
}
.flip-front { transform: rotateY(0deg); }
.flip-back  { transform: rotateY(180deg); }

/* Respect reduced motion */
@media (prefers-reduced-motion: reduce) {
  .flip-inner { transition: none; }
  .flip-inner.is-flipped { transform: rotateY(180deg); }
}
</style>
