<script setup lang="ts">
import type { PropType } from 'vue'

type Project = {
  title: string
  description: string
  tech: string[]
  link?: string
}

defineProps({
  projects: {
    type: Array as PropType<Project[]>,
    required: true,
  },
})
</script>

<template>
  <section id="projects" class="section alternate-bg">
    <div class="container">
      <h2 class="section-title">Featured Projects</h2>
      <div class="projects-grid">
        <div v-for="(project, index) in projects" :key="index" class="project-card">
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <div class="tech-stack">
            <span v-for="t in project.tech" :key="t">{{ t }}</span>
          </div>
          <a v-if="project.link" :href="project.link" class="project-link">View Project &rarr;</a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container {
  max-width: 1024px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* --- Sections --- */
.section {
  padding: 5rem 0;
}

.section-title {
  font-size: 2rem;
  margin-bottom: 3rem;
  position: relative;
  display: block;
  text-align: center;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background-color: #38bdf8;
  border-radius: 2px;
}

.alternate-bg {
  background-color: #1e293b;
}

/* --- Projects --- */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.project-card {
  background-color: #0f172a;
  padding: 2rem;
  border-radius: 8px;
  transition: transform 0.3s;
  border: 1px solid rgba(255, 255, 255, 0.05);
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translateY(-5px);
}

.project-card h3 {
  color: #e2e8f0;
  margin-bottom: 1rem;
}

.project-card p {
  color: #94a3b8;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
  flex-grow: 1;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-stack span {
  font-size: 0.8rem;
  color: #38bdf8;
}

.project-link {
  color: #e2e8f0;
  text-decoration: none;
  border-bottom: 1px solid transparent;
  transition: border-color 0.3s;
  align-self: flex-start;
}

.project-link:hover {
  border-bottom-color: #38bdf8;
}
</style>
