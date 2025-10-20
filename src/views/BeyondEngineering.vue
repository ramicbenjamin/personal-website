<script setup lang="ts">
import { ref } from 'vue'
import unsaLogo from '@/assets/unsa_logo.svg'
import etfLogo from '@/assets/etf_logo.svg'

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

type Notable = {
  title: string
  org: string
  orgUrl?: string
  startDate: string
  endDate: string | null
  location: string
  blurb?: string
  highlights?: string[]
  responsibilities?: string[]
  linkText?: string
  linkHref?: string
  technologies?: string[]
}

type Interest = {
  title: string
  description: string
  gradient: string
}

const education = ref<Education[]>([
  {
    degree: "Master's degree (MEng), Computer Science and Informatics",
    dates: '2017 – 2019',
    faculty: 'Faculty of Electrical Engineering',
    facultyUrl: 'https://www.etf.unsa.ba/',
    facultyLogo: etfLogo,
    university: 'University of Sarajevo',
    universityUrl: 'https://www.unsa.ba/',
    universityLogo: unsaLogo,
    department: 'Department for Computer Science and Informatics',
    description:
      'Focused on advanced concepts in software architecture, distributed systems, and cybersecurity. The program combined theoretical research with practical work on secure, scalable software systems and data protection.',
  },
  {
    degree: "Bachelor's degree (BEng), Computer Science and Informatics",
    dates: '2014 – 2017',
    faculty: 'Faculty of Electrical Engineering',
    facultyUrl: 'https://www.etf.unsa.ba/',
    facultyLogo: etfLogo,
    university: 'University of Sarajevo',
    universityUrl: 'https://www.unsa.ba/',
    universityLogo: unsaLogo,
    department: 'Department for Computer Science and Informatics',
    description:
      'Built a strong foundation in programming, algorithms, and systems design, along with software engineering principles that shaped my technical mindset and analytical problem-solving approach.',
  },
])

const notableProjects = ref<Notable[]>([
  {
    title: 'Fundraising Team Leader',
    org: 'ValueUp: Mind Your Own Business',
    startDate: '2016-12-01',
    endDate: '2017-05-01',
    location: 'Sarajevo · Voluntary',
    blurb:
      'Educationally motivating conference bringing together youth in Bosnia and Herzegovina with domestic and international startup founders and experts.',
    highlights: ['See Conference Aftermovie'],
    linkText: 'See Conference Aftermovie',
    linkHref: 'https://www.youtube.com/watch?v=_CxzyQUY8ZU',
    responsibilities: [
      'Planned and organized conference activities from concept to execution.',
      'Managed budget, fundraising, and donor relations.',
      'Pitched to sponsors and investors and developed financing strategies.',
      'Coordinated volunteers and communicated with speakers.',
      'Created and managed the conference schedule.'
    ]
  },
  {
    title: 'Local Committee Coordinator',
    org: 'Mozaik Foundation · Youth Bank',
    orgUrl: 'https://mozaik.ba/en/',
    startDate: '2011-03-01',
    endDate: '2014-10-01',
    location: 'Sarajevo and Doboj Jug · Voluntary',
    blurb:
      'Youth Bank is a program by the Mozaik Foundation that empowers thousands of young people each year through community work.',
    highlights: ['Rated in TOP 10 young leaders among all local committees.'],
    responsibilities: [
      'Led coordination between the local committee and the head organization, ensuring smooth communication and project alignment.',
      'Collaborated with the local community to identify key issues and define actionable strategies for improvement.',
      'Guided and educated youth on preparing detailed project proposals to secure funding for community initiatives.',
      'Reviewed and approved project applications, overseeing budget allocation and financing decisions.',
      'Supervised and tracked project activities from initiation to completion, ensuring goals and timelines were met.'
    ]
  }
])

const interests = ref<Interest[]>([
  {
    title: 'Basketball & Sports',
    gradient: 'from-emerald-700 to-emerald-500',
    description:
      'Basketball has always been a big part of my life. I grew up playing in youth leagues and still enjoy getting on the court now and then. More than anything, it taught me how teamwork really works — how communication, trust, and effort come together to reach a goal. These days I’m more into individual sports like padel, tennis, and weight training, which help me stay energized.'
  },
  {
    title: 'Photo Studio & Video Editing',
    gradient: 'from-amber-600 to-yellow-500',
    description:
      'In high school, I spent about three years working at a photo studio, editing wedding videos and handling post-production. I used tools like Adobe Premiere Pro, After Effects, and Photoshop, and that’s where I developed an eye for rhythm, detail, and storytelling. That creative background still shapes how I think about design, structure, and problem-solving in software today.'
  },
  {
    title: 'Filmmaking & Storycraft',
    gradient: 'from-rose-700 to-rose-500',
    description:
      'Together with friends, I wrote and produced short films, including both documentaries and fictional stories. Turning an idea into something real taught me how to plan, collaborate, and adapt when things didn’t go as expected. Like software development, filmmaking is all about balancing creativity and structure to bring ideas to life.'
  },
  {
    title: 'Volunteering & Community',
    gradient: 'from-indigo-700 to-indigo-500',
    description:
      'For more than a decade, I’ve been active in volunteering and community work, helping local projects grow both educationally and infrastructurally. I’ve collaborated with schools, universities, local communities, and NGOs to create learning opportunities and support youth initiatives. Over the years, I’ve been a part of organizing events, workshops, and meetups to connect people around shared goals.'
  }
])

function formatDate(date: Date) {
  const months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
  return `${months[date.getMonth()]} ${date.getFullYear()}`
}
function calculateLongevity(startDate: string, endDate: string) {
  const s = new Date(startDate)
  const e = new Date(endDate)
  let years = e.getFullYear() - s.getFullYear()
  let months = e.getMonth() - s.getMonth()
  if (months < 0) { years -= 1; months += 12 }
  const y = years > 0 ? `${years} year${years > 1 ? 's' : ''}` : ''
  const m = months > 0 ? `${months} month${months > 1 ? 's' : ''}` : ''
  return [y, m].filter(Boolean).join(', ')
}
function formatDateRange(startDate: string, endDate: string | null) {
  const start = formatDate(new Date(startDate))
  const end = endDate ? formatDate(new Date(endDate)) : 'Present'
  const longevity = calculateLongevity(startDate, endDate || new Date().toISOString())
  return `${start} - ${end} · ${longevity}`
}
function isVoluntary(location: string) {
  return /voluntary/i.test(location)
}
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

      <div class="mt-12">
        <h2 class="text-2xl md:text-3xl font-bold tracking-wide mb-6 text-teal-400">Education</h2>
        <div class="grid gap-6 md:grid-cols-2">
          <article
            v-for="(ed, i) in education"
            :key="i"
            class="rounded-2xl ring-1 ring-white/10 overflow-hidden bg-slate-900/40 backdrop-blur"
          >
            <div class="p-6 bg-gradient-to-br text-white"
                 :class="i % 2 === 0 ? 'from-blue-700 to-cyan-600' : 'from-purple-700 to-pink-600'">
              <div class="flex items-center gap-3 mb-4">
                <div v-if="ed.universityLogo || ed.facultyLogo" class="flex items-center gap-3">
                  <img v-if="ed.universityLogo" :src="ed.universityLogo" class="h-10 w-10 rounded-full ring-1 ring-white/20 p-1" />
                  <img v-if="ed.facultyLogo" :src="ed.facultyLogo" class="h-10 w-10 rounded-full ring-1 ring-white/20 p-1" />
                </div>
              </div>
              <h3 class="text-lg font-semibold leading-snug">{{ ed.degree }}</h3>
              <p class="text-xs text-white/80 mt-1">{{ ed.dates }}</p>
            </div>
            <div class="px-6 py-5">
              <p class="text-gray-300 mb-2">
                <strong class="text-gray-100">
                  <a :href="ed.facultyUrl" target="_blank" class="text-teal-300 underline hover:decoration-teal-300">{{ ed.faculty }}</a>
                </strong>
                <span class="text-gray-400">, </span>
                <a :href="ed.universityUrl" target="_blank" class="text-teal-300 underline hover:decoration-teal-300">{{ ed.university }}</a>
              </p>
              <p class="text-gray-400 text-sm mb-1">{{ ed.department }}</p>
              <p class="text-gray-300">{{ ed.description }}</p>
            </div>
          </article>
        </div>
      </div>

      <div class="mt-14">
        <h2 class="text-2xl md:text-3xl font-bold tracking-wide mb-6">
          <span class="text-teal-400">Notable</span> Projects &amp; Community Work
        </h2>

        <div class="space-y-6">
          <article
            v-for="(project, i) in notableProjects"
            :key="project.title + i"
            class="rounded-2xl ring-1 ring-white/10 overflow-hidden bg-slate-900/40 backdrop-blur"
          >
            <div class="p-6 bg-gradient-to-br text-white"
                 :class="[
                   i % 5 === 0 && 'from-emerald-700 to-emerald-500',
                   i % 5 === 1 && 'from-rose-700 to-rose-500',
                   i % 5 === 2 && 'from-indigo-700 to-indigo-500',
                   i % 5 === 3 && 'from-amber-600 to-yellow-500',
                   i % 5 === 4 && 'from-teal-700 to-teal-500'
                 ]">
              <div class="flex items-start justify-between gap-3">
                <div class="min-w-0">
                  <h3 class="text-lg md:text-xl font-semibold">{{ project.title }}</h3>
                  <p class="text-sm text-white/90">
                    <a v-if="project.orgUrl" :href="project.orgUrl" target="_blank"
                       class="underline decoration-white/30 hover:decoration-white">{{ project.org }}</a>
                    <span v-else>{{ project.org }}</span>
                  </p>
                  <p class="text-xs md:text-sm text-white/80 mt-0.5">
                    {{ project.location }}
                    <span v-if="isVoluntary(project.location)"
                          class="ml-2 px-2 py-0.5 rounded-full bg-white/20 text-[11px]">Voluntary</span>
                  </p>
                  <p class="text-xs md:text-sm text-white/80">{{ formatDateRange(project.startDate, project.endDate) }}</p>
                </div>
              </div>
            </div>

            <div class="px-6 py-5 space-y-4">
              <p v-if="project.blurb" class="text-gray-200">{{ project.blurb }}</p>
              <ul v-if="project.highlights?.length" class="list-disc pl-5 text-gray-100 space-y-1.5">
                <li v-for="(h, hi) in project.highlights" :key="hi">
                  <a v-if="project.linkText && project.linkHref && h === project.linkText"
                     :href="project.linkHref" target="_blank"
                     class="text-teal-300 underline hover:decoration-teal-300">{{ h }}</a>
                  <span v-else>{{ h }}</span>
                </li>
              </ul>
              <div v-if="project.responsibilities?.length">
                <p class="font-semibold text-gray-200 mb-1">Responsibilities</p>
                <ul class="list-disc pl-5 text-gray-200 space-y-1.5">
                  <li v-for="(r, ri) in project.responsibilities" :key="ri">{{ r }}</li>
                </ul>
              </div>
            </div>
          </article>
        </div>
      </div>

      <div class="mt-14">
        <div class="grid gap-6 md:grid-cols-2">
          <article
            v-for="(interest, i) in interests"
            :key="i"
            class="rounded-2xl ring-1 ring-white/10 overflow-hidden"
          >
            <div class="p-6 bg-gradient-to-br text-white" :class="interest.gradient">
              <h2 class="text-xl md:text-2xl font-bold leading-snug">{{ interest.title }}</h2>
            </div>
            <div class="px-6 py-5 bg-slate-900/40 backdrop-blur">
              <p class="text-gray-200">{{ interest.description }}</p>
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>
