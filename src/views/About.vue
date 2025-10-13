<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'
import axios from 'axios'
import SocialLinks from '@/components/SocialLinks.vue'

const props = withDefaults(defineProps<{
  stackUserId?: number
  showSocial?: boolean
}>(), {
  stackUserId: 7770919,
  showSocial: false,
})

const reputation = ref<number | null>(null)
const loading = ref(true)
const err = ref<string | null>(null)

const stackProfileUrl = computed(
  () => `https://stackoverflow.com/users/${props.stackUserId}`
)
const numberFmt = new Intl.NumberFormat()

onMounted(async () => {
  try {
    const resp = await axios.get(
      `https://api.stackexchange.com/2.3/users/${props.stackUserId}?site=stackoverflow`
    )
    const item = resp?.data?.items?.[0]
    reputation.value = typeof item?.reputation === 'number' ? item.reputation : null
  } catch (e) {
    // Non-fatal; we just show '—'
    err.value = 'Failed to load reputation'
    // console.error(e)
  } finally {
    loading.value = false
  }
})
</script>

<template>
  <!-- Inherit site background; just use section blocks -->
  <section class="w-full px-6 py-12">
    <!-- Header -->
    <div class="text-center space-y-6">
      <h1 class="text-4xl md:text-6xl font-extrabold tracking-wide">
        About <span class="text-teal-400">Me</span>
      </h1>
      <p class="text-lg md:text-xl text-gray-300 max-w-3xl mx-auto">
        I’m <span class="text-teal-400 font-bold">Benjamin Ramić</span>, a passionate and driven software engineer with a
        proven track record of developing scalable applications and fostering growth within teams. Over the years, I’ve
        combined technical depth with leadership and mentoring to help businesses achieve their goals efficiently and
        innovatively.
      </p>
    </div>

    <!-- Career Highlights -->
    <div class="mt-12 max-w-5xl w-full mx-auto space-y-6">
      <h2 class="text-3xl font-bold text-teal-400">Career Highlights</h2>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div class="bg-gradient-to-br from-teal-700 to-teal-500 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Proven Leadership</h3>
          <p class="mt-4 text-gray-100">
            Led software engineering teams, driving innovation and collaboration. Mentored developers and built processes that
            empower teams to deliver exceptional results.
          </p>
        </div>

        <div class="bg-gradient-to-br from-blue-700 to-blue-500 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Technical Excellence</h3>
          <p class="mt-4 text-gray-100">
            Grounded in core engineering principles, clear abstractions, sound architecture, and thoughtful trade-offs, to deliver maintainable, performant, and user-centered systems that scale.
          </p>
        </div>

        <div class="bg-gradient-to-br from-gray-800 to-gray-700 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Innovative Solutions</h3>
          <p class="mt-4 text-gray-100">
            Transitioned legacy systems to modern platforms, improving scalability and performance while minimizing risk.
          </p>
        </div>

        <div class="bg-gradient-to-br from-purple-700 to-purple-500 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Cross-Functional Collaboration</h3>
          <p class="mt-4 text-gray-100">
            Translate business goals into technical plans and ensure alignment across stakeholders.
          </p>
        </div>

        <div class="bg-gradient-to-br from-orange-700 to-orange-500 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Community Engagement</h3>
          <p class="mt-4 text-gray-100">
            10+ years of volunteering and knowledge sharing across the internet and open-source communities.
            <span class="block mt-2">
              StackOverflow reputation:
              <span class="font-bold">
                <template v-if="loading">Loading…</template>
                <template v-else-if="reputation !== null">{{ numberFmt.format(reputation) }}</template>
                <template v-else>—</template>
              </span>
            </span>
          </p>
          <a
            :href="stackProfileUrl"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center mt-4 text-white hover:underline"
            aria-label="View my StackOverflow profile"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="currentColor" viewBox="0 0 24 24">
              <path d="M17.32 20.45h-10.6V14.7H4.8v8.7h14.4v-8.7h-1.88v5.75zM7.28 18.35h8.45v-1.8H7.28v1.8zm.33-3.42l8.23 1.71.37-1.76-8.22-1.71-.38 1.76zm1.17-4.13l7.5 3.42.76-1.67-7.5-3.42-.76 1.67zm2.28-4.07l6.36 5.1 1.16-1.45-6.35-5.11-1.17 1.46zM14.9 3l-1.55 1.24 5.12 6.39 1.54-1.25L14.9 3z"/>
            </svg>
            View My StackOverflow Profile
          </a>
        </div>

        <div class="bg-gradient-to-br from-green-700 to-green-500 p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Lifelong Learning</h3>
          <p class="mt-4 text-gray-100">
            Constantly evolving through courses, workshops, and self-driven projects to stay ahead of industry trends.
          </p>
        </div>
      </div>
    </div>

    <!-- Personal Philosophy -->
    <div class="mt-12 max-w-5xl w-full mx-auto space-y-6 text-center">
      <h2 class="text-3xl font-bold text-teal-400">Personal Philosophy</h2>
      <p class="text-lg text-gray-300">
        I’m passionate about building software—and <span class="text-teal-400 font-bold">relationships</span>. I create
        environments where people thrive, fostering trust and <span class="text-teal-400 font-bold">driving innovation
        through collaboration</span>. I value mentorship and helping others grow.
      </p>
    </div>

    <!-- Skills -->
    <div class="mt-12 max-w-5xl w-full mx-auto space-y-6">
      <h2 class="text-3xl font-bold text-teal-400">Skills and Expertise</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div class="bg-gradient-to-br from-blue-700 to-blue-500 text-white p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Core Skills</h3>
          <ul class="mt-4 list-disc list-inside">
            <li>Front-end Development</li>
            <li>Back-end Architecture</li>
            <li>Database Design</li>
            <li>API Design & Integration</li>
            <li>Cloud Infrastructure</li>
            <li>Performance Optimization</li>
            <li>Code Reviews & Standards</li>
          </ul>
        </div>

        <div class="bg-gradient-to-br from-gray-800 to-gray-700 text-white p-6 rounded-lg shadow ring-1 ring-white/10">
          <h3 class="text-xl font-bold">Soft Skills</h3>
          <ul class="mt-4 list-disc list-inside">
            <li>Team Leadership</li>
            <li>Mentorship & Coaching</li>
            <li>Cross-functional Collaboration</li>
            <li>Problem Solving</li>
            <li>Effective Communication</li>
            <li>Adaptability</li>
            <li>Strategic Planning</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Current Technologies -->
    <div class="mt-16 text-center px-6 max-w-5xl mx-auto">
      <h2 class="text-3xl font-bold text-teal-400 mb-6">🛠️ Current Technologies & Tools</h2>
      <div class="flex flex-wrap justify-center gap-4">
        <img src="https://img.shields.io/badge/Laravel-F55247?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel">
        <img src="https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="AWS">
        <img src="https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
        <img src="https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D" alt="Vue.js">
        <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
        <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript">
      </div>
    </div>

    <!-- Worked With -->
    <div class="mt-12 text-center px-6 max-w-5xl mx-auto">
      <h2 class="text-3xl font-bold text-teal-400 mb-6">📚 Technologies & Tools that I Worked With</h2>
      <div class="flex flex-wrap justify-center gap-4">
        <img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black" alt="C">
        <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
        <img src="https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white" alt="C#">
        <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android">
        <img src="https://img.shields.io/badge/Ionic-3880FF?style=for-the-badge&logo=ionic&logoColor=white" alt="Ionic">
        <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js">
        <img src="https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white" alt="Angular">
        <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React">
        <img src="https://img.shields.io/badge/.NET_Framework-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET Framework">
        <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java">
        <img src="https://img.shields.io/badge/MySQL-007396?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
        <img src="https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python">
      </div>
    </div>

    <!-- Contact -->
    <div class="mt-12 max-w-5xl w-full mx-auto space-y-6 text-center">
      <h2 class="text-3xl font-bold text-teal-400">Contact Me</h2>
      <p class="text-lg text-gray-300">
        Like what you see? If something here sparks your interest or you need friendly/professional advice, reach out.
        Whether it’s a quick question or a deeper dive, I’m happy to help. Drop me a message on any of my social profiles!
      </p>

      <div v-if="props.showSocial" class="mt-6">
        <SocialLinks />
      </div>
    </div>
  </section>
</template>
