<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { RouterLink } from 'vue-router';
import axios from 'axios';

// State to hold StackOverflow reputation
const reputation = ref(null);

// Fetch StackOverflow reputation on component mount
onMounted(async () => {
  try {
    const response = await axios.get('https://api.stackexchange.com/2.3/users/7770919?site=stackoverflow');
    reputation.value = response.data.items[0].reputation;
  } catch (error) {
    console.error('Error fetching StackOverflow reputation:', error);
  }
});
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-900 via-gray-800 to-slate-900 text-white flex flex-col items-center p-6">
    <!-- Header Section -->
    <section class="text-center mt-12 space-y-6">
      <h1 class="text-4xl md:text-6xl font-extrabold tracking-wide">
        About <span class="text-teal-400">Me</span>
      </h1>
      <p class="text-lg md:text-xl text-gray-300 max-w-3xl">
        I’m <span class="text-teal-400 font-bold">Benjamin Ramić</span>, a passionate and driven software engineer with a proven track record of developing scalable applications and fostering growth within teams. Over the years, I’ve mastered the art of combining technical expertise with leadership and mentoring, enabling businesses to achieve their goals efficiently and innovatively.
      </p>
    </section>

    <!-- Career Highlights Section -->
    <section class="mt-12 max-w-5xl w-full space-y-6">
      <h2 class="text-3xl font-bold text-teal-400">Career Highlights</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div class="bg-gradient-to-br from-teal-700 to-teal-500 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Proven Leadership</h3>
          <p class="mt-4 text-gray-100">
            Successfully led software engineering teams, driving innovation and fostering a collaborative environment. Skilled in mentoring junior developers and building processes that empower teams to deliver exceptional results.
          </p>
        </div>
        <div class="bg-gradient-to-br from-blue-700 to-blue-500 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Technical Excellence</h3>
          <p class="mt-4 text-gray-100">
            Expertise in modern technologies like Vue.js, Laravel, AWS, and PostgreSQL, with a focus on crafting clean, efficient, and user-friendly solutions that scale.
          </p>
        </div>
        <div class="bg-gradient-to-br from-gray-800 to-gray-700 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Innovative Solutions</h3>
          <p class="mt-4 text-gray-100">
            Played a pivotal role in transitioning legacy systems to modern platforms, ensuring seamless scalability and performance improvements.
          </p>
        </div>
        <div class="bg-gradient-to-br from-purple-700 to-purple-500 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Cross-Functional Collaboration</h3>
          <p class="mt-4 text-gray-100">
            Skilled at working with cross-functional teams, translating business requirements into technical tasks, and ensuring alignment across stakeholders.
          </p>
        </div>
        <!-- Orange Card -->
        <div class="bg-gradient-to-br from-orange-700 to-orange-500 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Community Engagement</h3>
          <p class="mt-4 text-gray-100">
            Committed over 10 years to volunteering and giving back to the community. Passionate about helping others by sharing knowledge on StackOverflow, with a reputation score of <span class="font-bold">{{ reputation !== null ? reputation : 'Loading...' }}</span>.
          </p>
          <a
            href="https://stackoverflow.com/users/7770919/ben"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center mt-4 text-white hover:underline"
          >
            <!-- StackOverflow Icon -->
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="currentColor" viewBox="0 0 24 24">
              <path d="M17.32 20.45h-10.6V14.7H4.8v8.7h14.4v-8.7h-1.88v5.75zM7.28 18.35h8.45v-1.8H7.28v1.8zm.33-3.42l8.23 1.71.37-1.76-8.22-1.71-.38 1.76zm1.17-4.13l7.5 3.42.76-1.67-7.5-3.42-.76 1.67zm2.28-4.07l6.36 5.1 1.16-1.45-6.35-5.11-1.17 1.46zM14.9 3l-1.55 1.24 5.12 6.39 1.54-1.25L14.9 3z"/>
            </svg>
            View My StackOverflow Profile
          </a>
        </div>
        <!-- New Card -->
        <div class="bg-gradient-to-br from-green-700 to-green-500 p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Lifelong Learning</h3>
          <p class="mt-4 text-gray-100">
            Dedicated to continuous improvement and staying ahead of industry trends. Actively pursuing new knowledge through courses, workshops, and self-driven projects to enhance skills and inspire innovation.
          </p>
        </div>
      </div>
    </section>

    <!-- Personal Philosophy Section -->
    <section class="mt-12 max-w-5xl w-full space-y-6">
      <h2 class="text-3xl font-bold text-teal-400">Personal Philosophy</h2>
      <p class="text-lg text-gray-300">
        My passion lies not just in building software but in building relationships. I believe in creating environments where individuals can thrive, fostering trust, and driving innovation through collaboration. I value mentorship and take pride in helping others grow, both professionally and personally.
      </p>
    </section>

    <!-- Skills and Expertise Section -->
    <section class="mt-12 max-w-5xl w-full space-y-6">
      <h2 class="text-3xl font-bold text-teal-400">Skills and Expertise</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="bg-gradient-to-br from-blue-700 to-blue-500 text-white p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Core Skills</h3>
          <ul class="mt-4 list-disc list-inside">
            <li>Front-end Development</li>
            <li>Back-end Architecture</li>
            <li>Database Design</li>
            <li>API Design & Integration</li>
          </ul>
        </div>
        <div class="bg-gradient-to-br from-teal-700 to-teal-500 text-white p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Technologies</h3>
          <ul class="mt-4 list-disc list-inside">
            <li>Vue.js</li>
            <li>Laravel</li>
            <li>AWS</li>
            <li>PostgreSQL / MySQL</li>
          </ul>
        </div>
        <div class="bg-gradient-to-br from-gray-800 to-gray-700 text-white p-6 rounded-lg shadow">
          <h3 class="text-xl font-bold">Soft Skills</h3>
          <ul class="mt-4 list-disc list-inside">
            <li>Team Leadership</li>
            <li>Mentorship & Coaching</li>
            <li>Cross-functional Collaboration</li>
            <li>Problem Solving</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Call to Action Section -->
    <section class="mt-12">
      <RouterLink
        to="/"
        class="bg-blue-500 text-black px-8 py-3 rounded-full font-medium text-lg shadow-lg hover:shadow-xl hover:bg-blue-400 transition-transform transform hover:scale-105"
      >
        Back to Home
      </RouterLink>
    </section>
  </div>
</template>
