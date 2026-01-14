<script setup lang="ts">
defineProps<{
  skills: string[]
}>()
</script>

<template>
  <section id="skills" class="section">
    <div class="container">
      <h2 class="section-title">Technical Skills</h2>
      <div class="skills-grid">
        <span v-for="skill in skills" :key="skill" class="skill-tag">
          {{ skill }}
        </span>
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

/* --- Skills --- */
.skills-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.skill-tag {
  background-color: #1e293b;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  color: #38bdf8;
  font-family: monospace;
  border: 1px solid rgba(56, 189, 248, 0.2);
}
</style>
