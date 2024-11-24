<script setup lang="ts">
import { ref } from 'vue';

// State to track hover
const isHovered = ref(false);

// File download link
const downloadLink = "https://drive.google.com/uc?id=1JkZoBMCCXTzVPZGU6oNfAm-EKyiTQYqQ&export=download";
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
      I thrive in collaborative environments where innovation meets execution. My experience extends beyond writing code; I’m skilled at fostering growth within teams, mentoring developers, and designing processes that drive success.
    </p>

    <!-- Action Buttons -->
    <div class="mt-10 flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-6">
      <RouterLink
        to="/about"
        class="bg-teal-400 text-black px-8 py-3 rounded-full text-center font-medium text-lg shadow-lg hover:shadow-xl hover:bg-teal-300 transition-transform transform hover:scale-105"
      >
        About Me
      </RouterLink>
      <RouterLink
        to="/experience"
        class="bg-blue-500 text-black px-8 py-3 rounded-full font-medium text-center text-lg shadow-lg hover:shadow-xl hover:bg-blue-400 transition-transform transform hover:scale-105"
      >
        My Work Experience
      </RouterLink>
    </div>

    <!-- Social Media Links -->
    <div class="mt-6 flex space-x-4">
      <a
        href="https://github.com/ramicbenjamin"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- GitHub Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- GitHub SVG Path -->
          <path
            d="M12 .5C5.64.5.5 5.64.5 12c0 5.08 3.29 9.39 7.84 10.91.57.11.78-.25.78-.55 0-.27-.01-1.01-.01-1.98-3.19.69-3.87-1.54-3.87-1.54-.52-1.33-1.27-1.69-1.27-1.69-1.04-.71.08-.7.08-.7 1.15.08 1.76 1.19 1.76 1.19 1.02 1.75 2.68 1.24 3.33.95.1-.74.4-1.24.72-1.52-2.55-.29-5.24-1.28-5.24-5.7 0-1.26.45-2.28 1.19-3.08-.12-.3-.52-1.5.11-3.13 0 0 .97-.31 3.19 1.18a11.12 11.12 0 012.9-.39c.98 0 1.98.13 2.9.39 2.21-1.5 3.18-1.18 3.18-1.18.63 1.63.23 2.83.11 3.13.74.8 1.19 1.82 1.19 3.08 0 4.43-2.7 5.41-5.26 5.69.41.35.78 1.03.78 2.08 0 1.5-.01 2.71-.01 3.08 0 .31.21.67.79.55A10.51 10.51 0 0023.5 12c0-6.36-5.14-11.5-11.5-11.5z"
          />
        </svg>
      </a>
      <a
        href="https://www.facebook.com/ramic.benjamin/"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- Facebook Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- Facebook SVG Path -->
          <path
            d="M22.675 0h-21.35C.596 0 0 .592 0 1.324v21.352C0 23.408.596 24 1.325 24h11.5v-9.294H9.692V11.13h3.133V8.413c0-3.1 1.894-4.788 4.659-4.788 1.325 0 2.462.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.577h-3.12V24h6.116C23.405 24 24 23.408 24 22.676V1.324C24 .592 23.405 0 22.675 0z"
          />
        </svg>
      </a>
      <a
        href="https://x.com/ramic_benjamin"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- X.com Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- X.com (Twitter) SVG Path -->
          <path d="M23.954 4.569c-.885.392-1.83.656-2.825.775 1.014-.611 1.794-1.574 2.163-2.723-.949.564-2.004.974-3.127 1.196-.896-.957-2.173-1.555-3.591-1.555-2.72 0-4.924 2.204-4.924 4.923 0 .386.045.762.127 1.124C7.691 8.094 4.066 6.128 1.64 3.161c-.423.723-.666 1.561-.666 2.475 0 1.708.869 3.213 2.188 4.096-.807-.026-1.566-.248-2.229-.616v.061c0 2.385 1.693 4.374 3.946 4.828-.413.112-.849.171-1.296.171-.314 0-.615-.03-.916-.086.631 1.953 2.445 3.377 4.604 3.416-1.68 1.318-3.809 2.105-6.102 2.105-.395 0-.785-.023-1.17-.068 2.189 1.394 4.768 2.209 7.557 2.209 9.054 0 14-7.498 14-13.986 0-.21 0-.423-.016-.634.961-.695 1.8-1.562 2.462-2.549z"/>
        </svg>
      </a>
      <a
        href="https://www.instagram.com/ramic.benjamin"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- Instagram Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- Instagram SVG Path -->
          <path
            d="M7.75 2h8.5A5.75 5.75 0 0 1 22 7.75v8.5A5.75 5.75 0 0 1 16.25 22h-8.5A5.75 5.75 0 0 1 2 16.25v-8.5A5.75 5.75 0 0 1 7.75 2zm0 1.5A4.25 4.25 0 0 0 3.5 7.75v8.5A4.25 4.25 0 0 0 7.75 20.5h8.5A4.25 4.25 0 0 0 20.5 16.25v-8.5A4.25 4.25 0 0 0 16.25 3.5h-8.5zM12 7a5 5 0 1 1 0 10 5 5 0 0 1 0-10zm0 1.5a3.5 3.5 0 1 0 0 7 3.5 3.5 0 0 0 0-7zm4.75-3a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"
          />
        </svg>
      </a>
      <a
        href="https://stackoverflow.com/users/7770919/ben"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- StackOverflow Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- StackOverflow SVG Path -->
          <path
            d="M17.32 20.45h-10.6V14.7H4.8v8.7h14.4v-8.7h-1.88v5.75zM7.28 18.35h8.45v-1.8H7.28v1.8zm.33-3.42l8.23 1.71.37-1.76-8.22-1.71-.38 1.76zm1.17-4.13l7.5 3.42.76-1.67-7.5-3.42-.76 1.67zm2.28-4.07l6.36 5.1 1.16-1.45-6.35-5.11-1.17 1.46zM14.9 3l-1.55 1.24 5.12 6.39 1.54-1.25L14.9 3z"
          />
        </svg>
      </a>
      <a
        href="https://www.linkedin.com/in/ramicbenjamin/"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-white transition-colors"
      >
        <!-- LinkedIn Icon -->
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
          <!-- LinkedIn SVG Path -->
          <path
            d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.762 2.239 5 5 5h14c2.762 0 5-2.238 5-5v-14c0-2.761-2.238-5-5-5zm-11.615 20.385h-3.385v-10.769h3.385v10.769zm-1.692-12.308c-1.091 0-1.975-.885-1.975-1.976s.884-1.975 1.975-1.975c1.091 0 1.975.884 1.975 1.975s-.884 1.976-1.975 1.976zm13.308 12.308h-3.385v-5.385c0-1.28-.026-2.927-1.781-2.927-1.782 0-2.055 1.391-2.055 2.829v5.483h-3.385v-10.769h3.252v1.472h.046c.452-.857 1.558-1.758 3.206-1.758 3.427 0 4.056 2.257 4.056 5.193v6.862z"
          />
        </svg>
      </a>
    </div>
  </div>
</template>
