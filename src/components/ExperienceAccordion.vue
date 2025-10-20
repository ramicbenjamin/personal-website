<script setup lang="ts">
import { ref } from 'vue'

export type Role = {
  title: string
  employmentType: string
  location: string
  startDate: string
  endDate: string | null
  responsibilities?: string[]
}

export type CompanyGroup = {
  company: string
  companyUrl?: string
  technologies?: string[]
  roles: Role[]
}

const props = defineProps<{
  companyGroups: CompanyGroup[]
}>()

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

function getCompanyStartDate(company: CompanyGroup) {
  return company.roles.map(r => r.startDate).sort()[0]
}
function getCompanyEndDate(company: CompanyGroup) {
  if (company.roles.some(r => r.endDate === null)) return null
  return company.roles.map(r => r.endDate as string).filter(Boolean).sort().slice(-1)[0] || null
}
function getCompanyDateRange(company: CompanyGroup) {
  return formatDateRange(getCompanyStartDate(company), getCompanyEndDate(company))
}
function getCompanyLocation(company: CompanyGroup) {
  const sorted = [...company.roles].sort((a, b) =>
    (b.endDate ?? '9999-12-31').localeCompare(a.endDate ?? '9999-12-31')
  )
  return sorted[0]?.location || company.roles[0]?.location || ''
}

function badgeForTechnology(technology: string): { src: string; alt: string } {
  const normalized = (technology || '').trim()
  const aliasToCanonical: Record<string, string> = {
    'Vue': 'Vue.js','VueJS': 'Vue.js','Vue Js': 'Vue.js',
    'TS': 'TypeScript',
    'Tailwind': 'Tailwind CSS','TailwindCSS': 'Tailwind CSS',
    'Postgres': 'PostgreSQL','PostgreSQL DB': 'PostgreSQL',
    'JS': 'JavaScript',
    '.NET': '.NET Framework','DotNet': '.NET Framework','.NET Framework': '.NET Framework',
    'C Sharp': 'C#','C-Sharp': 'C#',
    'Node': 'Node.js','NodeJS': 'Node.js','Node Js': 'Node.js',
    'Ionic 2': 'Ionic','Ionic Framework': 'Ionic',
    'Amazon Web Services': 'AWS',
    'Oracle DB': 'Oracle','Oracle Database': 'Oracle',
    'HTML5': 'HTML','CSS3': 'CSS',
    'Github': 'GitHub',
    'ReactJS': 'React','React.js': 'React',
    'SequelizeJS': 'Sequelize'
  }
  const canonical = aliasToCanonical[normalized] ?? normalized
  const map: Record<string, string> = {
    'Laravel': 'https://img.shields.io/badge/Laravel-F55247?style=for-the-badge&logo=laravel&logoColor=white',
    'Vue.js': 'https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D',
    'TypeScript': 'https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white',
    'Tailwind CSS': 'https://img.shields.io/badge/Tailwind%20CSS-38B2AC?style=for-the-badge&logo=tailwindcss&logoColor=white',
    'MySQL': 'https://img.shields.io/badge/MySQL-007396?style=for-the-badge&logo=mysql&logoColor=white',
    'PostgreSQL': 'https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white',
    'AWS': 'https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white',
    'JavaScript': 'https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black',
    'React': 'https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black',
    'Angular': 'https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white',
    'Node.js': 'https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white',
    'Ionic': 'https://img.shields.io/badge/Ionic-3880FF?style=for-the-badge&logo=ionic&logoColor=white',
    'C': 'https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black',
    'C++': 'https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white',
    'C#': 'https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white',
    'Android': 'https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white',
    '.NET Framework': 'https://img.shields.io/badge/.NET_Framework-512BD4?style=for-the-badge&logo=dotnet&logoColor=white',
    'Java': 'https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white',
    'Python': 'https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54',
    'Sequelize': 'https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white',
    'Oracle': 'https://img.shields.io/badge/Oracle_DB-F80000?style=for-the-badge&logo=oracle&logoColor=white',
    'Git': 'https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white',
    'GitHub': 'https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white',
    'HTML': 'https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white',
    'CSS': 'https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white',
    'AWS Lambda': 'https://img.shields.io/badge/AWS%20Lambda-FF9900?style=for-the-badge&logo=awslambda&logoColor=white',
    'REST APIs': 'https://img.shields.io/badge/REST_APIs-02569B?style=for-the-badge&logo=apachespark&logoColor=white'
  }
  const url = map[canonical]
  if (url) return { src: url, alt: canonical }
  const label = encodeURIComponent(canonical)
  return { src: `https://img.shields.io/badge/${label}-555?style=for-the-badge`, alt: canonical }
}

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

const openCompanies = ref<Set<number>>(new Set())
function toggleCompanyAccordion(companyIndex: number) {
  const updated = new Set(openCompanies.value)
  updated.has(companyIndex) ? updated.delete(companyIndex) : updated.add(companyIndex)
  openCompanies.value = updated
}
function isCompanyAccordionOpen(companyIndex: number) {
  return openCompanies.value.has(companyIndex)
}

function roleCountLabel(count: number) {
  return count === 1 ? '1 role' : `${count} roles`
}
</script>

<template>
  <div class="space-y-8">
    <article
      v-for="(company, companyIndex) in props.companyGroups"
      :key="`${company.company}-${companyIndex}`"
      class="rounded-2xl ring-1 ring-white/10 overflow-hidden"
    >
      <button
        class="group w-full text-left cursor-pointer"
        :aria-expanded="isCompanyAccordionOpen(companyIndex) ? 'true' : 'false'"
        :aria-controls="`company-panel-${companyIndex}`"
        :aria-label="`${company.company}: ${isCompanyAccordionOpen(companyIndex) ? 'Hide details' : 'See more'} (${roleCountLabel(company.roles.length)})`"
        @click="toggleCompanyAccordion(companyIndex)"
      >
        <div
          class="p-6 md:p-7 bg-gradient-to-br text-white flex flex-col gap-2.5"
          :class="headerGradients[companyIndex % headerGradients.length]"
        >
          <div class="flex items-start justify-between gap-4">
            <div class="min-w-0">
              <h3 class="font-bold text-2xl leading-snug break-words">
                <template v-if="company.companyUrl">
                  <a
                    :href="company.companyUrl"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="underline decoration-white/30 hover:decoration-white"
                  >{{ company.company }}</a>
                </template>
                <template v-else>{{ company.company }}</template>
              </h3>
              <p class="text-sm md:text-base text-white/85 break-words">{{ getCompanyLocation(company) }}</p>
              <p class="text-sm md:text-base text-white/80 break-words">{{ getCompanyDateRange(company) }}</p>
            </div>

            <div class="flex flex-col items-end gap-1">
              <svg
                class="h-6 w-6 md:h-7 md:w-7 flex-shrink-0 transition-transform"
                :class="isCompanyAccordionOpen(companyIndex) ? 'rotate-180' : ''"
                xmlns="http://www.w3.org/2000/svg"
                fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"
              >
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
              </svg>
              <span
                class="hidden md:inline-flex items-center gap-1 rounded-full bg-white/15 px-2 py-0.5 text-xs text-white/90 tracking-wide"
              >
                <span v-if="!isCompanyAccordionOpen(companyIndex)">Click to see more</span>
                <span v-else>Click to hide</span>
                <span aria-hidden="true">·</span>
                <span>{{ roleCountLabel(company.roles.length) }}</span>
              </span>
            </div>
          </div>

          <div v-if="company.technologies?.length" class="flex flex-wrap gap-2 mt-2">
            <img
              v-for="technology in company.technologies"
              :key="`${company.company}-${technology}`"
              :src="badgeForTechnology(technology).src"
              :alt="badgeForTechnology(technology).alt"
              class="h-7"
              loading="lazy"
              decoding="async"
            />
          </div>
        </div>
      </button>

      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 -translate-y-1"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-1"
      >
        <div
          v-show="isCompanyAccordionOpen(companyIndex)"
          :id="`company-panel-${companyIndex}`"
          class="bg-slate-900/40 backdrop-blur px-6 md:px-8 py-6 md:py-8"
        >
          <div class="space-y-8 md:space-y-10">
            <section
              v-for="(role, roleIndex) in company.roles"
              :key="`${role.title}-${role.startDate}-${roleIndex}`"
              class="space-y-3 md:space-y-4"
            >
              <h4 class="text-lg md:text-xl font-semibold text-slate-100 leading-tight break-words">
                {{ role.title }}
                <span class="text-slate-400 font-normal"> · {{ role.employmentType }}</span>
              </h4>

              <p class="text-sm md:text-base text-slate-400 leading-relaxed flex flex-wrap gap-x-2">
                <span class="break-words">{{ role.location }}</span>
                <span aria-hidden="true">•</span>
                <span class="break-words">{{ formatDateRange(role.startDate, role.endDate) }}</span>
              </p>

              <ul
                v-if="role.responsibilities?.length"
                class="list-disc pl-5 md:pl-6 text-slate-200 leading-relaxed space-y-1.5 md:space-y-2"
              >
                <li
                  v-for="(responsibility, responsibilityIndex) in role.responsibilities"
                  :key="`${role.title}-${responsibilityIndex}`"
                  class="break-words"
                >
                  {{ responsibility }}
                </li>
              </ul>
            </section>
          </div>
        </div>
      </transition>
    </article>
  </div>
</template>
