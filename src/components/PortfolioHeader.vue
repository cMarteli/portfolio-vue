<script setup lang="ts">
import { ref } from 'vue'

const navOpen = ref(false)

const toggleNav = () => {
  navOpen.value = !navOpen.value
}

const scrollToSection = (id: string) => {
  navOpen.value = false // close menu on mobile
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <header class="navbar">
    <div class="container nav-content">
      <div class="logo" @click="scrollToSection('hero')">&lt;VMarteli /&gt;</div>

      <button class="mobile-toggle" @click="toggleNav" aria-label="Toggle navigation">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>

      <nav :class="{ 'nav-links': true, 'nav-active': navOpen }">
        <a href="#about" @click.prevent="scrollToSection('about')">About</a>
        <a href="#skills" @click.prevent="scrollToSection('skills')">Skills</a>
        <a href="#projects" @click.prevent="scrollToSection('projects')">Projects</a>
        <a href="#contact" @click.prevent="scrollToSection('contact')">Contact</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.container {
  max-width: 1024px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* --- Navigation --- */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  height: 70px;
  background-color: rgba(15, 23, 42, 0.9);
  backdrop-filter: blur(10px);
  z-index: 1000;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.nav-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: #38bdf8;
  cursor: pointer;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-links a {
  color: #e2e8f0;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-links a:hover {
  color: #38bdf8;
}

.mobile-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  flex-direction: column;
  gap: 5px;
}

.bar {
  width: 25px;
  height: 3px;
  background-color: #e2e8f0;
  border-radius: 2px;
}

/* --- Responsive --- */
@media (max-width: 768px) {
  .mobile-toggle {
    display: flex;
  }

  .nav-links {
    position: fixed;
    top: 70px;
    right: 0;
    height: calc(100vh - 70px);
    background-color: #1e293b;
    flex-direction: column;
    width: 100%;
    align-items: center;
    justify-content: center;
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
  }

  .nav-active {
    transform: translateX(0);
  }
}
</style>
