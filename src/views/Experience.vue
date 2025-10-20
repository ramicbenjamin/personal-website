<script setup lang="ts">
import { ref } from 'vue'
import ExperienceAccordion from '@/components/ExperienceAccordion.vue'

type Role = {
  title: string
  employmentType: string
  location: string
  startDate: string
  endDate: string | null
  responsibilities?: string[]
}

type CompanyGroup = {
  company: string
  companyUrl?: string
  technologies?: string[]
  roles: Role[]
}

const companyGroups = ref<CompanyGroup[]>([
  {
    company: 'RSVPify',
    companyUrl: 'https://rsvpify.com/',
    technologies: ['Laravel','Vue.js','TypeScript','Tailwind CSS','MySQL','PostgreSQL','AWS', 'Git'],
    roles: [
      {
        title: 'Senior Full Stack Software Engineer / Pod Leader',
        employmentType: 'Full-time',
        location: 'Chicago, Illinois, United States · Remote',
        startDate: '2025-01-01',
        endDate: null, // Present
        responsibilities: [
          'Combined senior-level technical ownership with leadership and coordination responsibilities. Oversaw a cross-functional pod, driving technical excellence, process improvement, and mentorship.',
          'Led a multidisciplinary engineering pod, balancing hands-on development with technical guidance and mentorship.',
          'Owned long-term architectural vision and system design to ensure performance, maintainability, and future scalability.',
          'Rebuilt and extended the platform for B2B and B2C audiences, introducing enterprise infrastructure, advanced integrations, and compliance-ready workflows.',
          'Implemented a role and permissions system for B2B users, enabling easier extension to different organizational roles.',
          'Implemented integrations with various CRM systems, as well as payment and charge processing systems supporting multiple payment providers.',
          'Introduced multi-layered email security checks to protect domain reputation and ensure integrity in high-volume communications, resulting in over a 90% reduction in spam reports.',
          'Applied LLMs and AI-driven automation to enhance email and communication security, detect anomalies, and monitor message integrity in real time.',
          'Established the Sarajevo Engineering Office, coordinating operations, finding the place, ensuring seamless remote collaboration, and promoting knowledge sharing.',
          'Refined agile workflows and delivery processes to improve delivery speed, transparency, and cross-team alignment.',
          'Collaborated with engineers at ChangeTower, RSVPify’s sister company, to drive cross-product innovation and unify engineering standards.'
        ]
      },
      {
        title: 'Senior Fullstack Software Engineer',
        employmentType: 'Full-time',
        location: 'Chicago, Illinois, United States · Remote',
        startDate: '2022-12-01',
        endDate: '2025-01-01',
        responsibilities: [
          'Responsible for complete software lifecycle ownership—from concept and architecture to deployment. Focused on designing scalable systems, mentoring engineers, and building enterprise-grade infrastructure and features.',
          'Designed and engineered the full software lifecycle, including database design, frontend and backend systems, Dockerization, CI/CD pipelines, and quality assurance.',
          'Rebuilt and extended the platform for both B2B and B2C audiences, introducing enterprise infrastructure, advanced integrations, and compliance-ready workflows while collaborating with product, design, and customer success teams.',
          'Owned technical design and long-term architecture to ensure maintainability and scalability across multiple product versions.',
          'Developed modular, framework-like code to reduce maintenance overhead and accelerate new feature delivery.',
          'Designed and developed a robust file management system, including conversion pipelines and file pre-optimization for performance and reliability.',
          'Partnered with product, design, and leadership teams to translate complex business needs into robust, production-grade solutions.',
          'Scaled the engineering team through hiring, onboarding, and mentoring, fostering a high-performance and learning-oriented culture.',
          'Promoted continuous learning through documentation, mentoring, and internal knowledge-sharing sessions.'
        ]
      },
      {
        title: 'Full Stack Engineer',
        employmentType: 'Full-time',
        location: 'Chicago, Illinois, United States · Remote',
        startDate: '2019-07-01',
        endDate: '2022-12-01',
        responsibilities: [
          'Full ownership of end-to-end features, architecture modernization, and major product expansion. Played a key role in the transition from legacy systems to the new replatformed core, enabling large-scale growth.',
          'Part of the core team that led the transition from the previous app version to a new replatformed core using modern technologies. This laid the foundation for company-wide growth in users, revenue, and team size, enabling RSVPify to evolve from a small startup to a globally recognized platform.',
          'Developed and deployed the Recurring Timeslots feature, enabling appointment scheduling and expanding the platform’s offering to new customer types.',
          'Maintained and developed multiple high-impact features, including seating charts, reporting dashboards, RSVP form security checks, schedule reminders, email invites, event check-ins, and limited-quantity controls.',
          'Helped define the roadmap and technical direction toward more B2B-focused features, preparing the next version of the platform for enterprise adoption.',
          'Maintained open-source libraries critical to RSVPify’s long-term performance and sustainability.',
          'Wrote and optimized database queries for data science projects.'
        ]
      },
      {
        title: 'Junior Fullstack Software Engineer',
        employmentType: 'Full-time',
        location: 'Chicago, Illinois, United States · Remote',
        startDate: '2018-01-01',
        endDate: '2019-07-01',
        responsibilities: [
          'Initial engineering role focused on maintaining early versions of the platform, implementing smaller features, and supporting the transition toward new architecture and technologies.',
          'Maintained the first versions of the RSVPify application by fixing bugs and developing smaller features to improve product stability.',
          'Collaborated with the team implementing the first ticket-selling system, allowing the company to take a new step toward replatforming and the creation of a greenfield project with modern technologies to support scalability and easier maintenance.',
          'Worked on payment systems, integrating Stripe and implementing 3D Secure to enhance transaction reliability and user trust.'
        ]
      }
    ]
  },
  {
    company: 'Faculty of Electrical Engineering University of Sarajevo',
    companyUrl: 'https://etf.unsa.ba/',
    technologies: ['Android','Java','MySQL','Oracle','.NET Framework','Python','Git'],
    roles: [
      {
        title: 'Undergraduate Teaching Assistant',
        employmentType: 'Part-time',
        location: 'Sarajevo, Federation of Bosnia and Herzegovina, Bosnia and Herzegovina · On-site',
        startDate: '2017-03-01',
        endDate: '2019-08-01',
        responsibilities: [
          'Early academic and technical role focused on supporting undergraduate courses in software engineering and database systems. Combined teaching, mentoring, and hands-on technical responsibilities to enhance student learning and maintain high teaching quality.',
          'Supported core computer science and engineering courses, including: Mobile Application Development (Razvoj mobilnih aplikacija), Development of Software Solutions (Razvoj programskih rješenja), Database Fundamentals (Osnove baza podataka)',
          'Prepared and maintained learning materials, lab assignments, and technical exercises, ensuring alignment with course objectives and real-world software practices.',
          'Set up and administered lab environments, including Android Studio, database systems, and network configurations, optimizing stability and accessibility for over 100 students per semester.',
          'Assisted professors during lectures and labs, helping students understand complex concepts through examples, debugging sessions, and practical demonstrations.',
          'Guided students in developing full-stack and mobile applications, mentoring teams on best practices in version control, software architecture, and database design.',
          'Taught students how to write and optimize SQL queries for relational database systems, focusing on performance and data integrity.',
          'Provided individualized mentoring and technical support, fostering problem-solving, collaboration, and critical thinking.',
          'Contributed to curriculum improvements, suggesting updates to lab content to incorporate modern technologies and tools.'
        ]
      }
    ]
  },
  {
    company: 'Pragmatio Solutions',
    companyUrl: 'https://www.linkedin.com/company/pragmatio-solutions/about/',
    technologies: ['Node.js','TypeScript','Sequelize','Ionic','MySQL','Git', 'Angular'],
    roles: [
      {
        title: 'Junior Software Engineer',
        employmentType: 'Part-time',
        location: 'Sarajevo · On-site',
        startDate: '2017-09-01',
        endDate: '2017-12-01',
        responsibilities: [
          'Developed mobile and backend applications for external clients using modern web and mobile technologies. Collaborated closely with teams and clients to deliver reliable, maintainable, and user-focused software solutions.',
          'Designed and implemented mobile and backend systems using Node.js, TypeScript, Sequelize, and Ionic 2.',
          'Built and maintained RESTful APIs and database models, ensuring scalability and data consistency.',
          'Developed the “Air Quality in Bosnia and Herzegovina” mobile app to visualize real-time environmental data, integrating live data feeds and geolocation features.',
          'Created the “Booking Summary” application for managing reservations and tracking availability in real time for airline reservations.',
          'Participated in the full development cycle, from requirement analysis and estimation to deployment and maintenance.',
          'Collaborated directly with clients to gather feedback, provide technical recommendations, and present regular progress updates.',
          'Engaged in agile sprints, code reviews, and QA processes to maintain high-quality standards and improve team velocity.',
          'Adapted quickly to new tools and evolving technology stacks, contributing to efficient project delivery and continuous improvement.'
        ]
      }
    ]
  }
])

</script>

<template>
  <section class="w-full px-6 py-12">
    <div class="mx-auto max-w-5xl">
      <h1 class="text-4xl md:text-5xl font-extrabold tracking-wide text-center mb-10">
        Ben's <span class="text-teal-400">Work Experience</span>
      </h1>

      <ExperienceAccordion :company-groups="companyGroups" />
    </div>
  </section>
</template>
