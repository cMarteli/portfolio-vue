<script setup lang="ts">
import type { PropType } from 'vue'
import resumePdf from '@/assets/pdf/resume.pdf'

type SocialLink = {
  name: string
  url: string
}


defineProps({
  socialLinks: {
    type: Array as PropType<SocialLink[]>,
    required: true,
  },
})
</script>

<template>
  <section id="contact" class="section">
    <div class="container contact-content">
      <h2 class="section-title">Get In Touch</h2>
      <p>
        Have any opportunities? Feel free to reach out
        via email or connect on LinkedIn.
      </p>
      <a :href="resumePdf" class="btn primary big-btn" download>Download Resume</a>

      <div class="social-links">
        <a
          v-for="link in socialLinks"
          :key="link.name"
          :href="link.url"
          target="_blank"
          class="social-link"
        >
          {{ link.name }}
        </a>
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

/* --- Buttons --- */
.btn {
  padding: 0.8rem 1.5rem;
  border-radius: 5px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  border: 1px solid #38bdf8;
  font-size: 1rem;
}

.btn.primary {
  background-color: #38bdf8;
  color: #0f172a;
}

.btn.primary:hover {
  background-color: #0ea5e9;
}

/* --- Contact --- */
.contact-content {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.contact-content p {
  margin-bottom: 2rem;
  color: #94a3b8;
}

.big-btn {
  padding: 1rem 2rem;
  font-size: 1.1rem;
  text-decoration: none;
  display: inline-block;
}

.social-links {
  margin-top: 3rem;
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.social-link {
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: #38bdf8;
}
</style>
