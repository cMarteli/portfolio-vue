<script setup lang="ts">
import { ref, onMounted } from 'vue'
import PortfolioHeader from './components/PortfolioHeader.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import PortfolioFooter from './components/PortfolioFooter.vue'

// --- Data ---

const skills = ref([
  'Java',
  'Kotlin',
  'C#',
  'Python',
  'JavaScript / TypeScript',
  'Angular',
  'Node.js',
  'Azure DevOps',
  'Docker',
  '.NET Core',
  'SQL',
])

// Mapped from Resume Projects
const projects = ref([
  {
    title: 'IMDEX Design Token System',
    description:
      'Internship project involving the design and creation of a design token system seamlessly integrated with Figma. Led an Agile team and managed stakeholder reporting.',
    tech: ['Angular', 'Express JS', 'Azure DevOps'],
    link: '#',
  },
  {
    title: 'Android Photo Gallery',
    description:
      'High Distinction university project. A photo gallery app with web search (Pixlr API) and cloud storage. Garnered 1k+ downloads on Google Play.',
    tech: ['Kotlin', 'Android SDK', 'Firebase'],
    link: 'https://github.com/cmarteli', // TODO; Add repo link
  },
  {
    title: '.NET Chat Application',
    description:
      'A robust .NET Core chat application leveraging MVC architecture and RESTful API. Focused on code quality and maintainability.',
    tech: ['C#', '.NET Core', 'REST API'],
    link: 'https://github.com/cmarteli',
  },
  {
    title: 'MaberseBot',
    description:
      'Versatile Discord bot integrating various APIs for RNG dice rolls, weather forecasts, and entertainment.',
    tech: ['Python', 'Flask', 'Discord API'],
    link: 'https://github.com/cmarteli',
  },
])

const socialLinks = ref([
  { name: 'GitHub', url: 'https://github.com/cmarteli' },
  { name: 'LinkedIn', url: 'https://linkedin.com/in/cmarteli' },
  { name: 'Email', url: 'mailto:caio.marteli@proton.me' },
])

// --- Lifecycle ---
onMounted(() => {
  console.log('Portfolio mounted')
})
</script>

<template>
  <div class="app-container">
    <PortfolioHeader />
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection :skills="skills" />
      <ProjectsSection :projects="projects" />
      <ContactSection :socialLinks="socialLinks" />
    </main>
    <PortfolioFooter />
  </div>
</template>

<style scoped>
/* --- Variables & Reset --- */
:root {
  --bg-color: #0f172a;
  --bg-alt: #1e293b;
  --text-main: #e2e8f0;
  --text-muted: #94a3b8;
  --accent: #38bdf8;
  --accent-hover: #0ea5e9;
  --nav-height: 70px;
}

* {
  box-sizing: border-box;
}

.app-container {
  font-family:
    'Inter',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    Oxygen,
    Ubuntu,
    Cantarell,
    'Open Sans',
    'Helvetica Neue',
    sans-serif;
  background-color: #0f172a;
  color: #e2e8f0;
  min-height: 100vh;
  line-height: 1.6;
}

.container {
  max-width: 1024px;
  margin: 0 auto;
  padding: 0 2rem;
}
</style>
