<!-- src/views/Experience.vue -->
<script setup lang="ts">
import { ref } from 'vue'

type Experience = {
  title: string
  company: string
  companyUrl?: string
  employmentType: string
  location: string
  startDate: string
  endDate: string | null
  subPosition?: string
  technologies?: string[]
  projects?: string[]
  responsibilities?: string[]
  courses?: string[]
  blurb?: string
  contactNote?: string
}

const experiences = ref<Experience[]>([
  {
    title: 'Full Stack Software Engineer',
    company: 'RSVPify',
    companyUrl: 'https://rsvpify.com/',
    employmentType: 'Full-time',
    location: 'Chicago, US · Remote',
    startDate: '2018-01-01',
    endDate: '2025-10-01',
    subPosition: 'Manager of people and culture',
    technologies: ['Laravel', 'Vue.js', 'TypeScript', 'Tailwind CSS', 'MySQL', 'PostgreSQL', 'AWS'],
    projects: ['Event management platform'],
    blurb:
      'RSVPify is an end-to-end event management platform trusted by Fortune 500s, nonprofits, and public sector orgs. It powers branded event pages, digital invitations, real-time RSVPs, and fast check-ins via QR codes or lookups.',
    contactNote: 'Contact information for referees who can confirm references available upon request.',
    responsibilities: [
      'Designed and engineered the full software lifecycle from concept to deployment (DB design, FE/BE systems, Dockerization, CI/CD, QA).',
      'Led project-based engineering teams building enterprise-grade features focused on scalability, reliability, and performance.',
      'Rebuilt and extended the platform for B2B and B2C audiences; introduced enterprise infrastructure, advanced integrations, and compliance-ready workflows while collaborating with product, design, and customer success.',
      'Owned technical design and long-term architecture to ensure maintainability and scalability across versions.',
      'Helped establish the Sarajevo Engineering Office; coordinated operations to strengthen collaboration, enable smooth remote work, and promote knowledge sharing.',
      'Scaled the team through hiring, onboarding, and mentoring; fostered a high-performance, learning-oriented culture.',
      'Refined workflows and agile practices to improve delivery speed, transparency, and team alignment.',
      'Worked with product, design, and leadership to translate complex business needs into robust, production-grade solutions.',
      'Advised and brainstormed with engineers at ChangeTower (sister company) to drive cross-product innovation and shared standards.',
      'Implemented multi-layered email security to protect domain reputation and ensure integrity in high-volume communications.',
      'Applied LLMs and AI-driven automation to enhance security checks, detect anomalies, and monitor communications in real time.',
      'Developed modular, framework-like code to reduce maintenance and accelerate feature delivery.',
      'Maintained open-source libraries critical to performance and long-term sustainability.',
      'Promoted continuous learning via documentation, mentoring, and knowledge-sharing sessions.'
    ]
  },
  {
    title: 'Undergraduate Teaching Assistant',
    company: 'Faculty of Electrical Engineering University of Sarajevo',
    companyUrl: 'https://etf.unsa.ba/',
    employmentType: 'Part-time',
    location: 'Sarajevo, BA · On-site',
    startDate: '2017-03-01',
    endDate: '2019-08-01',
    technologies: ['MySQL', 'Oracle', 'C#', '.NET Framework', 'Java', 'Android'],
    courses: [
      'Development of mobile applications',
      'Development of software solutions',
      'Database fundamentals'
    ],
    blurb:
      'The Faculty of Electrical Engineering, University of Sarajevo, is the oldest and largest institution in Bosnia and Herzegovina educating across electrical engineering and computer science.',
    contactNote: 'Contact information for referees who can confirm references available upon request.',
    responsibilities: [
      'Prepared learning materials, lab tasks, and assignments aligned with course objectives.',
      'Set up and maintained technical equipment and software environments for classes.',
      'Assisted in lectures and labs; helped students understand key concepts via hands-on work.',
      'Supervised group activities and guided students in collaborative project development.',
      'Mentored students across the semester, providing technical guidance and feedback.'
    ]
  },
  {
    title: 'Student Software Developer',
    company: 'Pragmatio Solutions',
    companyUrl: 'https://www.linkedin.com/company/pragmatio-solutions/about/',
    employmentType: 'Part-time',
    location: 'Sarajevo, BA · On-site',
    startDate: '2017-09-01',
    endDate: '2017-12-31',
    technologies: ['Node.js', 'Sequelize', 'TypeScript', 'Ionic', 'Angular'],
    projects: ['Air Quality in Bosnia and Herzegovina', 'Booking summary'],
    blurb:
      'Pragmatio Solutions delivered high-quality near-shore outsourcing opportunities to customers around Europe.',
    responsibilities: [
      'Developed frontend and backend software for external clients across varied stacks.',
      'Quickly learned new tools and adapted to different project requirements.',
      'Communicated with clients, presented updates, and aligned development with feedback.',
      'Participated in code reviews, QA, and sprint planning to improve code quality and delivery.',
      'Contributed to estimation discussions and agile sprint organization.'
    ]
  }
])

/* ------------------ Notable Projects ------------------ */
type Notable = {
  title: string
  org: string
  orgUrl?: string
  startDate: string
  endDate: string | null
  location: string
  blurb?: string
  highlights?: string[]           // bullet points (can include a linked item)
  responsibilities?: string[]
  linkText?: string               // when a highlight equals linkText, it becomes a link
  linkHref?: string
  contactNote?: string            // same style as jobs
  technologies?: string[]
}

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
    contactNote: 'Contact information for referees who can confirm references available upon request.',
    technologies: [],
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
    ],
    technologies: []
  }
])

/* --------- Accordion state --------- */
const openJobs = ref<Set<number>>(new Set())
const openNotables = ref<Set<number>>(new Set())

function toggleJob(idx: number) {
  const next = new Set(openJobs.value)
  if (next.has(idx)) { next.delete(idx) } else { next.add(idx) }
  openJobs.value = next
}
function isJobOpen(idx: number) { return openJobs.value.has(idx) }

function toggleNotable(idx: number) {
  const next = new Set(openNotables.value)
  if (next.has(idx)) { next.delete(idx) } else { next.add(idx) }
  openNotables.value = next
}
function isNotableOpen(idx: number) { return openNotables.value.has(idx) }

/* ------------------ Helpers ------------------ */
function formatDateRange(startDate: string, endDate: string | null) {
  const start = formatDate(new Date(startDate))
  const end = endDate ? formatDate(new Date(endDate)) : 'Present'
  const longevity = calculateLongevity(startDate, endDate || new Date().toISOString())
  return `${start} - ${end} · ${longevity}`
}
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

/* ------------------ Color palettes ------------------ */
const headerGradients = [
  'from-fuchsia-700 to-purple-600',
  'from-emerald-700 to-emerald-500',
  'from-indigo-700 to-indigo-500',
  'from-cyan-700 to-sky-500',
  'from-rose-700 to-rose-500',
  'from-amber-600 to-yellow-500',
  'from-teal-700 to-teal-500',
  'from-violet-700 to-violet-500',
  'from-slate-700 to-slate-500',
  'from-blue-700 to-blue-500'
]

/* ------------------ Shields.io badges ------------------ */
function badgeFor(tech: string): { src: string; alt: string } {
  const map: Record<string, string> = {
    'Laravel': 'https://img.shields.io/badge/Laravel-F55247?style=for-the-badge&logo=laravel&logoColor=white',
    'Vue.js': 'https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D',
    'TypeScript': 'https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white',
    'Tailwind CSS': 'https://img.shields.io/badge/Tailwind%20CSS-38B2AC?style=for-the-badge&logo=tailwindcss&logoColor=white',
    'MySQL': 'https://img.shields.io/badge/MySQL-007396?style=for-the-badge&logo=mysql&logoColor=white',
    'PostgreSQL': 'https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white',
    'AWS': 'https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white',
    'Node.js': 'https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white',
    'Sequelize': 'https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white',
    'Ionic': 'https://img.shields.io/badge/Ionic-3880FF?style=for-the-badge&logo=ionic&logoColor=white',
    'Angular': 'https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white',
    'React': 'https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black',
    'C': 'https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black',
    'C++': 'https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white',
    'C#': 'https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white',
    'Android': 'https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white',
    '.NET Framework': 'https://img.shields.io/badge/.NET_Framework-512BD4?style=for-the-badge&logo=dotnet&logoColor=white',
    'Java': 'https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white',
    'Python': 'https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54',
    'Oracle': 'https://img.shields.io/badge/Oracle_DB-F80000?style=for-the-badge&logo=oracle&logoColor=white'
  }
  const url = map[tech]
  if (url) return { src: url, alt: tech }
  const label = encodeURIComponent(tech)
  return { src: `https://img.shields.io/badge/${label}-555?style=for-the-badge`, alt: tech }
}
</script>

<template>
  <section class="w-full px-6 py-12">
    <div class="mx-auto max-w-5xl">
      <h1 class="text-4xl md:text-5xl font-extrabold tracking-wide text-center mb-10">
        Ben's <span class="text-teal-400">Work Experience</span>
      </h1>

      <!-- Jobs -->
      <div class="space-y-6">
        <article
          v-for="(exp, idx) in experiences"
          :key="idx"
          class="rounded-2xl ring-1 ring-white/10 overflow-hidden"
        >
          <!-- Header / Summary -->
          <button
            class="w-full text-left cursor-pointer"
            :aria-expanded="isJobOpen(idx) ? 'true' : 'false'"
            :aria-controls="`exp-panel-${idx}`"
            @click="toggleJob(idx)"
          >
            <div
              class="p-6 bg-gradient-to-br text-white flex flex-col gap-3"
              :class="headerGradients[idx % headerGradients.length]"
            >
              <div class="flex items-start justify-between gap-4">
                <div class="min-w-0">
                  <!-- Wrapped mobile title, no ellipsis -->
                  <h3 class="font-bold text-xl sm:text-2xl leading-snug break-words whitespace-normal">
                    {{ exp.title }}
                  </h3>
                  <p class="text-sm text-white/90 whitespace-normal break-words">
                    <template v-if="exp.companyUrl">
                      <a
                        :href="exp.companyUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="underline decoration-white/30 hover:decoration-white"
                      >{{ exp.company }}</a>
                    </template>
                    <template v-else>{{ exp.company }}</template>
                    · {{ exp.employmentType }}
                  </p>
                  <p class="text-sm text-white/80 whitespace-normal break-words">{{ exp.location }}</p>
                  <p class="text-sm text-white/80">
                    {{ formatDateRange(exp.startDate, exp.endDate) }}
                  </p>
                </div>

                <!-- Chevron -->
                <svg
                  class="h-6 w-6 flex-shrink-0 transition-transform"
                  :class="isJobOpen(idx) ? 'rotate-180' : ''"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"
                  aria-hidden="true"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                </svg>
              </div>

              <!-- Tech badges -->
              <div v-if="exp.technologies?.length" class="flex flex-wrap gap-2 mt-1">
                <img
                  v-for="tech in exp.technologies"
                  :key="tech"
                  :src="badgeFor(tech).src"
                  :alt="badgeFor(tech).alt"
                  class="h-7"
                  loading="lazy"
                  decoding="async"
                />
              </div>
            </div>
          </button>

          <!-- Details / Panel -->
          <transition
            enter-active-class="transition duration-200 ease-out"
            enter-from-class="opacity-0 -translate-y-1"
            enter-to-class="opacity-100 translate-y-0"
            leave-active-class="transition duration-150 ease-in"
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 -translate-y-1"
          >
            <div
              v-show="isJobOpen(idx)"
              :id="`exp-panel-${idx}`"
              role="region"
              class="bg-slate-900/40 backdrop-blur px-6 pb-6 pt-4"
            >
              <p v-if="exp.blurb" class="text-gray-200">
                <template v-if="exp.companyUrl">
                  <a
                    :href="exp.companyUrl"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="text-teal-300 underline decoration-teal-300/30 hover:decoration-teal-300"
                  >{{ exp.company }}</a>
                </template>
                <template v-else>{{ exp.company }}</template>
                &nbsp;— {{ exp.blurb }}
              </p>

              <p v-if="exp.subPosition" class="mt-3 text-gray-300">
                <span class="font-semibold">Sub-position:</span> {{ exp.subPosition }}
              </p>

              <p v-if="exp.contactNote" class="mt-3 text-gray-400 italic">
                {{ exp.contactNote }}
              </p>

              <div class="grid gap-6 md:grid-cols-2 mt-6">
                <div v-if="exp.projects?.length">
                  <p class="font-semibold text-gray-200">Projects</p>
                  <ul class="mt-2 list-disc list-inside text-gray-100">
                    <li v-for="p in exp.projects" :key="p">{{ p }}</li>
                  </ul>
                </div>

                <div v-if="exp.courses?.length">
                  <p class="font-semibold text-gray-200">Courses</p>
                  <ul class="mt-2 list-disc list-inside text-gray-100 space-y-1">
                    <li v-for="c in exp.courses" :key="c">{{ c }}</li>
                  </ul>
                </div>
              </div>

              <div v-if="exp.responsibilities?.length" class="mt-6">
                <p class="font-semibold text-gray-200">Responsibilities</p>
                <ul class="mt-2 list-disc list-inside text-gray-100 space-y-1">
                  <li v-for="r in exp.responsibilities" :key="r">{{ r }}</li>
                </ul>
              </div>
            </div>
          </transition>
        </article>
      </div>

      <!-- Notable Projects -->
      <div class="mt-14">
        <h2 class="text-2xl md:text-3xl font-bold tracking-wide mb-4">
          <span class="text-teal-400">Notable</span> Projects
        </h2>

        <div class="space-y-6">
          <article
            v-for="(n, i) in notableProjects"
            :key="i"
            class="rounded-2xl ring-1 ring-white/10 overflow-hidden"
          >
            <!-- Header -->
            <button
              class="w-full text-left cursor-pointer"
              :aria-expanded="isNotableOpen(i) ? 'true' : 'false'"
              :aria-controls="`notable-panel-${i}`"
              @click="toggleNotable(i)"
            >
              <div
                class="p-6 bg-gradient-to-br text-white flex flex-col gap-3"
                :class="headerGradients[(i + experiences.length) % headerGradients.length]"
              >
                <div class="flex items-start justify-between gap-4">
                  <div class="min-w-0">
                    <!-- Wrapped mobile title -->
                    <h3 class="font-semibold text-lg sm:text-xl leading-snug break-words whitespace-normal">
                      {{ n.title }}
                    </h3>
                    <p class="text-sm text-white/90 whitespace-normal break-words">
                      <template v-if="n.orgUrl">
                        <a
                          :href="n.orgUrl"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="underline decoration-white/30 hover:decoration-white"
                        >{{ n.org }}</a>
                      </template>
                      <template v-else>{{ n.org }}</template>
                    </p>
                    <p class="text-sm text-white/80 whitespace-normal break-words">
                      {{ formatDateRange(n.startDate, n.endDate) }} · {{ n.location }}
                    </p>
                  </div>

                  <svg
                    class="h-6 w-6 flex-shrink-0 transition-transform"
                    :class="isNotableOpen(i) ? 'rotate-180' : ''"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"
                    aria-hidden="true"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                  </svg>
                </div>
              </div>
            </button>

            <!-- Panel -->
            <transition
              enter-active-class="transition duration-200 ease-out"
              enter-from-class="opacity-0 -translate-y-1"
              enter-to-class="opacity-100 translate-y-0"
              leave-active-class="transition duration-150 ease-in"
              leave-from-class="opacity-100 translate-y-0"
              leave-to-class="opacity-0 -translate-y-1"
            >
              <div
                v-show="isNotableOpen(i)"
                :id="`notable-panel-${i}`"
                role="region"
                class="bg-slate-900/40 backdrop-blur px-6 pb-6 pt-4"
              >
                <p v-if="n.blurb" class="text-gray-200">{{ n.blurb }}</p>

                <!-- Highlights as bullets; if equals linkText, render as a link -->
                <ul v-if="n.highlights?.length" class="mt-3 list-disc list-inside text-gray-200 space-y-1">
                  <li v-for="h in n.highlights" :key="h">
                    <template v-if="n.linkText && n.linkHref && h === n.linkText">
                      <a :href="n.linkHref" target="_blank" rel="noopener noreferrer"
                         class="text-teal-300 underline decoration-teal-300/30 hover:decoration-teal-300">
                        {{ n.linkText }}
                      </a>
                    </template>
                    <template v-else>{{ h }}</template>
                  </li>
                </ul>

                <p v-if="n.contactNote" class="mt-3 text-gray-400 italic">
                  {{ n.contactNote }}
                </p>

                <div v-if="n.responsibilities?.length" class="mt-4">
                  <p class="font-semibold text-gray-200">Responsibilities</p>
                  <ul class="mt-2 list-disc list-inside text-gray-100 space-y-1">
                    <li v-for="r in n.responsibilities" :key="r">{{ r }}</li>
                  </ul>
                </div>
              </div>
            </transition>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>
