<script setup lang="ts">
import { ref, onMounted } from 'vue';

// --- Data ---

const navOpen = ref(false);

const toggleNav = () => {
  navOpen.value = !navOpen.value;
};

const scrollToSection = (id: string) => {
  navOpen.value = false; // close menu on mobile
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

const skills = ref([
  'JavaScript / TypeScript', 'Vue.js 3', 'Node.js', 'Python',
  'Docker', 'AWS', 'PostgreSQL', 'GraphQL', 'Git / CI/CD'
]);

const projects = ref([
  {
    title: 'Cloud Dashboard',
    description: 'A real-time analytics dashboard for cloud infrastructure monitoring.',
    tech: ['Vue 3', 'D3.js', 'AWS Lambda'],
    link: '#'
  },
  {
    title: 'E-Commerce API',
    description: 'Scalable RESTful API handling 10k+ requests/second.',
    tech: ['Node.js', 'Express', 'Redis', 'Docker'],
    link: '#'
  },
  {
    title: 'Task Master',
    description: 'Collaborative project management tool with live socket updates.',
    tech: ['TypeScript', 'Socket.io', 'MongoDB'],
    link: '#'
  }
]);

const socialLinks = ref([
  { name: 'GitHub', url: '#' },
  { name: 'LinkedIn', url: '#' },
  { name: 'Twitter', url: '#' },
  { name: 'Email', url: 'mailto:hello@example.com' }
]);

// --- Lifecycle ---
onMounted(() => {
  // Optional: Add interaction observers or animations here
  console.log('Portfolio mounted');
});
</script>

<template>
  <div class="app-container">
    <!-- Navigation -->
    <header class="navbar">
      <div class="container nav-content">
        <div class="logo" @click="scrollToSection('hero')">
          &lt;DevPortfolio /&gt;
        </div>
        
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

    <!-- Hero Section -->
    <section id="hero" class="hero-section">
      <div class="container hero-content">
        <h1 class="animate-fade-up">Hi, I'm <span class="highlight">Victor</span>.</h1>
        <h2 class="animate-fade-up delay-1">Full Stack Software Engineer.</h2>
        <p class="animate-fade-up delay-2">
          I build accessible, pixel-perfect, and performant web applications.
        </p>
        <div class="cta-group animate-fade-up delay-3">
          <button class="btn primary" @click="scrollToSection('projects')">View Work</button>
          <button class="btn secondary" @click="scrollToSection('contact')">Contact Me</button>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section alternate-bg">
      <div class="container">
        <h2 class="section-title">About Me</h2>
        <div class="about-grid">
          <div class="about-text">
            <p>
              I am a passionate developer based in Australia with a focus on creating efficient and scalable software solutions. 
              With a background in Computer Science, I enjoy tackling complex problems and turning them into simple, beautiful interface designs.
            </p>
            <p>
              When I'm not coding, you can find me exploring the outdoors, reading sci-fi novels, or experimenting with new tech stacks.
            </p>
          </div>
          <div class="about-visual">
             <!-- CSS-only placeholder for profile image -->
            <div class="profile-placeholder">
              <span>IMG</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
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

    <!-- Projects Section -->
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
            <a :href="project.link" class="project-link">View Project &rarr;</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
      <div class="container contact-content">
        <h2 class="section-title">Get In Touch</h2>
        <p>
          I'm currently looking for new opportunities. Whether you have a question or just want to say hi, 
          I'll try my best to get back to you!
        </p>
        <a href="mailto:hello@example.com" class="btn primary big-btn">Say Hello</a>
        
        <div class="social-links">
          <a v-for="link in socialLinks" :key="link.name" :href="link.url" class="social-link">
            {{ link.name }}
          </a>
        </div>
      </div>
    </section>

    <footer class="footer">
      <p>&copy; {{ new Date().getFullYear() }} Victor Developer. Built with Vue 3.</p>
    </footer>
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

/* Ensure the component takes standard resets if global css is missing */
* {
  box-sizing: border-box;
}

.app-container {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  background-color: #0f172a; /* Hardcoded fallback for var */
  color: #e2e8f0;
  min-height: 100vh;
  line-height: 1.6;
}

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
  border-bottom: 1px solid rgba(255,255,255,0.05);
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

/* --- Sections --- */
.section {
  padding: 5rem 0;
}

.section-title {
  font-size: 2rem;
  margin-bottom: 3rem;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 60px;
  height: 4px;
  background-color: #38bdf8;
  border-radius: 2px;
}

.alternate-bg {
  background-color: #1e293b;
}

/* --- About --- */
.about-grid {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: 4rem;
  align-items: center;
}

.profile-placeholder {
  width: 100%;
  aspect-ratio: 1/1;
  background-color: #334155;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid #38bdf8;
  color: #94a3b8;
  font-weight: bold;
  position: relative;
}

.profile-placeholder::after {
  content: '';
  position: absolute;
  top: 15px;
  left: 15px;
  right: -15px;
  bottom: -15px;
  border: 2px solid #38bdf8;
  border-radius: 10px;
  z-index: -1;
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
  border: 1px solid rgba(255,255,255,0.05);
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
}

.project-link:hover {
  border-bottom-color: #38bdf8;
}

/* --- Contact --- */
.contact-content {
  text-align: center;
  max-width: 600px;
}

.contact-content p {
  margin-bottom: 2rem;
  color: #94a3b8;
}

.big-btn {
  padding: 1rem 2rem;
  font-size: 1.1rem;
}

.social-links {
  margin-top: 3rem;
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.social-link {
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: #38bdf8;
}

.footer {
  text-align: center;
  padding: 2rem;
  color: #64748b;
  font-size: 0.9rem;
}

/* --- Animations --- */
.animate-fade-up {
  animation: fadeUp 0.8s ease-out forwards;
  opacity: 0;
  transform: translateY(20px);
}

.delay-1 { animation-delay: 0.1s; }
.delay-2 { animation-delay: 0.2s; }
.delay-3 { animation-delay: 0.3s; }

@keyframes fadeUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* --- Responsive --- */
@media (max-width: 768px) {
  .hero-content h1 { font-size: 2.5rem; }
  .hero-content h2 { font-size: 1.5rem; }
  .about-grid { grid-template-columns: 1fr; }
  .profile-placeholder { width: 80%; margin: 0 auto; }
  
  .mobile-toggle { display: flex; }
  
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