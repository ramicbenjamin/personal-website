<script setup lang="ts">
import { ref } from 'vue';
import SocialLinks from '@/components/SocialLinks.vue'

// State to track hover
const isHovered = ref(false);

// File download link
const downloadLink = "https://drive.google.com/uc?id=1oioZ9Vs6n0qzypORYAhtPSRXp9tORNQK&export=download";
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 text-white flex flex-col items-center justify-center p-6">
    <!-- Profile Image with Hover Effect -->
    <div
      class="w-48 h-48 rounded-full overflow-hidden shadow-lg relative cursor-pointer transition-transform transform hover:scale-105"
      @mouseover="isHovered = true"
      @mouseleave="isHovered = false"
    >
      <img
        v-if="!isHovered"
        src="@/assets/ben.png"
        alt="Benjamin Ramić"
        class="w-full h-full object-cover"
      />
      <a
        v-if="isHovered"
        :href="downloadLink"
        download
        class="absolute inset-0 flex items-center justify-center bg-black bg-opacity-75 text-white text-lg font-semibold transition-opacity"
      >
        Download My CV
      </a>
    </div>

    <!-- Main Title -->
    <h1 class="text-4xl md:text-6xl font-extrabold tracking-wide text-center mt-6">
      Hi, I’m <span class="text-teal-400">Benjamin Ramić</span>
    </h1>
    <p class="text-lg md:text-xl text-gray-300 text-center mt-4 max-w-2xl">
      I’m a passionate <span class="text-blue-400 font-bold">Software Engineer</span> with a proven track record of building scalable, efficient, and user-friendly software solutions. Over the years, I’ve developed a strong ability to work with teams and lead them toward achieving technical and business goals.
    </p>
    <p class="text-lg md:text-xl text-gray-300 text-center mt-4 max-w-2xl">
      I thrive in collaborative environments where innovation meets execution. My experience extends beyond writing code. I’m skilled at fostering growth within teams, mentoring developers, and designing processes that drive success.
    </p>

    <!-- Action Buttons -->
    <div class="mt-10 flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-6">
      <RouterLink
        to="/about"
        class="bg-teal-400 text-black px-8 py-3 rounded-full text-center font-medium text-lg shadow-lg hover:shadow-xl hover:bg-teal-300 transition-transform transform hover:scale-105"
      >
        Read More About Me
      </RouterLink>
      <RouterLink
        to="/experience"
        class="bg-blue-500 text-black px-8 py-3 rounded-full font-medium text-center text-lg shadow-lg hover:shadow-xl hover:bg-blue-400 transition-transform transform hover:scale-105"
      >
        My Work Experience
      </RouterLink>
    </div>

    <SocialLinks />

    <!-- Subtle Footer -->
    <footer class="mt-12 text-gray-500 text-sm">
      Copyright © {{ new Date().getFullYear() }} Benjamin Ramić
    </footer>
  </div>
</template>
