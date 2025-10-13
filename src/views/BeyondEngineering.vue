<!-- src/views/BeyondEngineering.vue -->
<script setup lang="ts">
import { ref } from 'vue'

// Import your logos
import unsaLogo from '@/assets/unsa_logo.svg'       // University of Sarajevo
import etfLogo from '@/assets/etf_logo.svg'         // Faculty of Electrical Engineering

type Education = {
  degree: string
  dates: string
  faculty: string
  facultyUrl: string
  facultyLogo?: string
  university: string
  universityUrl: string
  universityLogo?: string
  department: string
  description: string
}

const education = ref<Education[]>([
  {
    degree: 'Master of Engineering (MEng), Computer Software Engineering',
    dates: '2017 – 2019',
    faculty: 'Faculty of Electrical Engineering',
    facultyUrl: 'https://www.etf.unsa.ba/',
    facultyLogo: etfLogo,
    university: 'University of Sarajevo',
    universityUrl: 'https://www.unsa.ba/',
    universityLogo: unsaLogo,
    department: 'Department for Computer Science and Informatics',
    description:
      'Focused on advanced concepts in software architecture, distributed systems, and cybersecurity. The program combined theoretical research with practical work on secure, scalable software systems and data protection.'
  },
  {
    degree: 'Bachelor’s Degree, Computer Software Engineering',
    dates: '2014 – 2017',
    faculty: 'Faculty of Electrical Engineering',
    facultyUrl: 'https://www.etf.unsa.ba/',
    facultyLogo: etfLogo,
    university: 'University of Sarajevo',
    universityUrl: 'https://www.unsa.ba/',
    universityLogo: unsaLogo,
    department: 'Department for Computer Science and Informatics',
    description:
      'Built a strong foundation in programming, algorithms, and systems design, along with software engineering principles that shaped my technical mindset and analytical problem-solving approach.'
  }
])
</script>

<template>
  <section class="w-full px-6 py-12">
    <div class="mx-auto max-w-5xl">
      <h1 class="text-4xl md:text-5xl font-extrabold tracking-wide text-center">
        Beyond <span class="text-teal-400">Engineering</span>
      </h1>
      <p class="mt-4 text-center text-gray-300 max-w-3xl mx-auto">
        A glimpse into my academic journey and the creative and personal experiences that helped shape how I think, work, and grow.
      </p>

      <!-- Education -->
      <div class="mt-12">
        <h2 class="text-2xl md:text-3xl font-bold tracking-wide mb-6 text-teal-400">
          Education
        </h2>

        <div class="grid gap-6 md:grid-cols-2">
          <article
            v-for="(ed, i) in education"
            :key="i"
            class="rounded-2xl ring-1 ring-white/10 overflow-hidden bg-slate-900/40 backdrop-blur"
          >
            <div
              class="p-6 bg-gradient-to-br text-white"
              :class="i % 2 === 0 ? 'from-blue-700 to-cyan-600' : 'from-purple-700 to-pink-600'"
            >
              <!-- Logos -->
              <div class="flex items-center gap-3 mb-4">
                <div
                  v-if="ed.universityLogo || ed.facultyLogo"
                  class="flex items-center gap-3"
                >
                  <div
                    v-if="ed.universityLogo"
                    class="h-10 w-10 rounded-full bg-white/10 ring-1 ring-white/20 p-1 flex-shrink-0"
                  >
                    <img
                      :src="ed.universityLogo"
                      alt="University logo"
                      class="h-full w-full object-contain rounded-full"
                      loading="lazy"
                    />
                  </div>
                  <div
                    v-if="ed.facultyLogo"
                    class="h-10 w-10 rounded-full bg-white/10 ring-1 ring-white/20 p-1 flex-shrink-0"
                  >
                    <img
                      :src="ed.facultyLogo"
                      alt="Faculty logo"
                      class="h-full w-full object-contain rounded-full"
                      loading="lazy"
                    />
                  </div>
                </div>
              </div>

              <div>
                <h3 class="text-lg font-semibold leading-snug">{{ ed.degree }}</h3>
                <p class="text-xs text-white/80 mt-1">{{ ed.dates }}</p>
              </div>
            </div>

            <div class="px-6 py-5">
              <p class="text-gray-300 mb-2">
                <strong class="text-gray-100">
                  <a
                    :href="ed.facultyUrl"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="text-teal-300 underline decoration-teal-300/30 hover:decoration-teal-300"
                  >
                    {{ ed.faculty }}
                  </a>
                </strong>
                <span class="text-gray-400">, </span>
                <a
                  :href="ed.universityUrl"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-teal-300 underline decoration-teal-300/30 hover:decoration-teal-300"
                >
                  {{ ed.university }}
                </a>
              </p>
              <p class="text-gray-400 text-sm mb-1">
                {{ ed.department }}
              </p>
              <p class="text-gray-300">{{ ed.description }}</p>
            </div>
          </article>
        </div>
      </div>

      <!-- Hobbies and Interests -->
      <div class="mt-14 space-y-8">
        <!-- Basketball -->
        <article class="rounded-2xl ring-1 ring-white/10 overflow-hidden">
          <div class="p-6 bg-gradient-to-br from-emerald-700 to-emerald-500 text-white">
            <h2 class="text-xl md:text-2xl font-bold leading-snug">
              Basketball &amp; Sports
            </h2>
          </div>
          <div class="px-6 py-5 bg-slate-900/40 backdrop-blur">
            <p class="text-gray-200">
              Basketball has always been a big part of my life. I played in youth leagues growing up and still enjoy
              playing from time to time today, although I find the most joy in watching the game and following my favorite teams.
              Lately, I’ve shifted toward individual sports such as padel, tennis, and weight training, which help me stay focused,
              energized, and balanced.
            </p>
          </div>
        </article>

        <!-- Photo Studio -->
        <article class="rounded-2xl ring-1 ring-white/10 overflow-hidden">
          <div class="p-6 bg-gradient-to-br from-amber-600 to-yellow-500 text-white">
            <h2 class="text-xl md:text-2xl font-bold leading-snug">
              Photo Studio &amp; Video Editing
            </h2>
          </div>
          <div class="px-6 py-5 bg-slate-900/40 backdrop-blur">
            <p class="text-gray-200">
              During high school, I spent about three years working at a photo studio, where I edited wedding videos and
              worked on post-production. I used tools such as Adobe Premiere Pro, After Effects, and Photoshop, developing
              an eye for rhythm, detail, and storytelling. That creative experience continues to influence how I approach
              design, structure, and problem-solving in software.
            </p>
          </div>
        </article>

        <!-- Filmmaking -->
        <article class="rounded-2xl ring-1 ring-white/10 overflow-hidden">
          <div class="p-6 bg-gradient-to-br from-rose-700 to-rose-500 text-white">
            <h2 class="text-xl md:text-2xl font-bold leading-snug">
              Filmmaking &amp; Storycraft
            </h2>
          </div>
          <div class="px-6 py-5 bg-slate-900/40 backdrop-blur">
            <p class="text-gray-200">
              Together with friends, I wrote and produced short films, both documentaries and fictional stories.
              The process of turning an idea into something tangible taught me planning, teamwork, and adaptability.
              Much like software development, filmmaking is about balancing creativity and structure to build something
              meaningful from imagination.
            </p>
          </div>
        </article>

        <!-- Volunteering -->
        <article class="rounded-2xl ring-1 ring-white/10 overflow-hidden">
          <div class="p-6 bg-gradient-to-br from-indigo-700 to-indigo-500 text-white">
            <h2 class="text-xl md:text-2xl font-bold leading-snug">
              Volunteering &amp; Community
            </h2>
          </div>
          <div class="px-6 py-5 bg-slate-900/40 backdrop-blur">
            <p class="text-gray-200">
              For over a decade, I have been deeply involved in volunteering and community building, supporting local projects by helping
              strengthen the community both infrastructurally and educationally. I worked with school organizations, university organizations, local communities and NGOs to
              create learning opportunities, improve local initiatives, and foster collaboration among young people.
              I've hosted number of events, workshops, and meetups to bring people together around shared interests and goals.
              These experiences taught me leadership through service, the value of persistence, and how meaningful change often starts with small, consistent efforts.
            </p>
          </div>
        </article>

      </div>
    </div>
  </section>
</template>
