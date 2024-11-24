<script setup lang="ts">
// Define experiences as a static property
const experiences = [
  {
    title: "Full Stack Software Engineer",
    company: "RSVPify",
    employmentType: "Full-time",
    location: "Chicago, Illinois, United States · Remote",
    dates: "Jan 2018 - Present · 6 yrs 11 mos",
    technologies: ["PHP Laravel", "Vue", "MySQL/PostgreSQL", "AWS"],
    projects: ["Event management platform"],
    responsibilities: [
      "Designing and engineering the complete software development process from concept to deployment.",
      "Leading product versioning and transitioning from legacy application to new versions.",
      "Reviewing code and maintaining high coding standards across the organization.",
      "Planning new features and updates for the software product.",
      "Managing the end-to-end life cycle of the software product.",
      "Overseeing automated testing and providing feedback during development.",
      "Prioritizing tasks and translating business requests to engineering tasks.",
      "Mentoring junior engineers and organizing hiring and on-boarding processes."
    ]
  },
  {
    title: "Undergraduate Teaching Assistant",
    company: "Faculty of Electrical Engineering University of Sarajevo",
    employmentType: "Part-time",
    location: "Sarajevo, Bosnia and Herzegovina · On-site",
    dates: "Mar 2017 - Aug 2019 · 2 yrs 6 mos",
    courses: [
      "Mobile Application Development",
      "Development of Software Solutions",
      "Database Fundamentals"
    ],
    responsibilities: [
      "Preparing learning materials and tasks for students.",
      "Setting up equipment for lessons.",
      "Helping students understand the curriculum through interactive lectures.",
      "Supervising student group activities and mentoring on tasks."
    ]
  },
  {
    title: "Student Software Developer",
    company: "Pragmatio Solutions",
    employmentType: "Part-time",
    location: "Sarajevo · On-site",
    dates: "Sep 2017 - Dec 2017 · 4 mos",
    technologies: ["NodeJS + Sequelize + TypeScript", "Ionic 2"],
    projects: ["Air Quality in Bosnia and Herzegovina", "Booking Summary"],
    responsibilities: [
      "Developing frontend and backend software for external clients.",
      "Presenting incremental software updates to clients and managing communications.",
      "Planning software development sprint cycles and analyzing client requirements.",
      "Participating in code reviews and quality assurance activities."
    ]
  }
];

// Define specific gradient colors for each card
const colors = [
  "bg-gradient-to-br from-purple-700 to-purple-500",
  "bg-gradient-to-br from-blue-700 to-blue-500",
  "bg-gradient-to-br from-green-700 to-green-500"
];
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 text-white flex flex-col items-center p-6">
    <!-- Header -->
    <h1 class="text-4xl md:text-6xl font-extrabold text-center mt-12 tracking-wide">
      Ben's <span class="text-teal-400">Work Experience</span>
    </h1>
    <p class="mt-4 text-lg text-gray-300 max-w-3xl text-center">
      A professional journey through software engineering and mentoring roles.
    </p>

    <!-- Experience Cards -->
    <div class="mt-12 w-full max-w-5xl space-y-8">
      <div
        v-for="(experience, index) in experiences"
        :key="index"
        :class="[colors[index % colors.length], 'p-6 rounded-lg shadow text-white']"
      >
        <h3 class="text-2xl font-bold">{{ experience.title }}</h3>
        <p class="text-sm text-gray-200">{{ experience.company }} · {{ experience.employmentType }}</p>
        <p class="text-sm text-gray-200">{{ experience.location }}</p>
        <p class="text-sm text-gray-200">{{ experience.dates }}</p>

        <template v-if="experience.technologies">
          <p class="mt-4"><span class="font-bold">Technologies:</span></p>
          <ul class="list-disc list-inside text-gray-100 mt-2">
            <li v-for="tech in experience.technologies" :key="tech">{{ tech }}</li>
          </ul>
        </template>

        <template v-if="experience.projects">
          <p class="mt-4"><span class="font-bold">Projects:</span></p>
          <ul class="list-disc list-inside text-gray-100 mt-2">
            <li v-for="project in experience.projects" :key="project">{{ project }}</li>
          </ul>
        </template>

        <template v-if="experience.responsibilities">
          <p class="mt-4"><span class="font-bold">Responsibilities:</span></p>
          <ul class="list-disc list-inside text-gray-100 mt-2">
            <li v-for="responsibility in experience.responsibilities" :key="responsibility">{{ responsibility }}</li>
          </ul>
        </template>

        <template v-if="experience.courses">
          <p class="mt-4"><span class="font-bold">Courses:</span></p>
          <ul class="list-disc list-inside text-gray-100 mt-2">
            <li v-for="course in experience.courses" :key="course">{{ course }}</li>
          </ul>
        </template>
      </div>
    </div>

    <!-- Back to Home Button -->
    <div class="mt-12">
      <RouterLink
        to="/"
        class="bg-blue-500 text-black px-6 py-3 rounded-full font-medium text-lg shadow-lg hover:shadow-xl hover:bg-blue-400 transition-transform transform hover:scale-105"
      >
        Back to Home
      </RouterLink>
    </div>
  </div>
</template>
