<script setup lang="ts">
const scrollToSection = (id: string) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <section id="hero" class="hero-section">
    <div class="container hero-content">
      <h1 class="animate-fade-up">Hey, I'm <span class="highlight">Vic</span></h1>
      <h2 class="animate-fade-up delay-1">Software Engineer.</h2>
      <p class="animate-fade-up delay-2">
        Results-driven developer with a solid foundation in Java, Kotlin, C#, and JavaScript. I
        build hands-on innovative solutions for dynamic organisations.
      </p>
      <div class="cta-group animate-fade-up delay-3">
        <button class="btn primary" @click="scrollToSection('projects')">View Work</button>
        <button class="btn secondary" @click="scrollToSection('contact')">Contact Me</button>
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

/* --- Hero --- */
.hero-section {
  height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 70px;
}

.hero-content h1 {
  font-size: 4rem;
  margin-bottom: 0.5rem;
  line-height: 1.1;
}

.hero-content h2 {
  font-size: 2.5rem;
  color: #94a3b8;
  margin-bottom: 1.5rem;
}

.highlight {
  color: #38bdf8;
}

.hero-content p {
  max-width: 500px;
  color: #94a3b8;
  font-size: 1.1rem;
  margin-bottom: 2rem;
}

.cta-group {
  display: flex;
  gap: 1rem;
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

.btn.secondary {
  background-color: transparent;
  color: #38bdf8;
}

.btn.secondary:hover {
  background-color: rgba(56, 189, 248, 0.1);
}

/* --- Animations --- */
.animate-fade-up {
  animation: fadeUp 0.8s ease-out forwards;
  opacity: 0;
  transform: translateY(20px);
}

.delay-1 {
  animation-delay: 0.1s;
}
.delay-2 {
  animation-delay: 0.2s;
}
.delay-3 {
  animation-delay: 0.3s;
}

@keyframes fadeUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* --- Responsive --- */
@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2.5rem;
  }
  .hero-content h2 {
    font-size: 1.5rem;
  }
}
</style>
