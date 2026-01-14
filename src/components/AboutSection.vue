<template>
  <section id="about" class="section alternate-bg">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-grid">
        <div class="about-text">
          <p>
            I am a Software Engineer based in Western Australia with a Bachelor of Computing from
            Curtin University. I have hands-on industry experience as a Full Stack Developer at
            IMDEX Ltd, where I utilized Angular and Node.js to manage specialized hardware
            inventory systems.
          </p>
          <p>
            My background includes volunteering as a student mentor and working in network
            diagnostics at Aussie Broadband. I am fluent in English and Portuguese, and passionate
            about applying my diverse skill set to challenging technical projects.
          </p>
        </div>
        <div class="about-visual">
          <div class="profile-placeholder">
            <span>VM</span>
          </div>
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
  font-size: 2rem;
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

/* --- Responsive --- */
@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
  .profile-placeholder {
    width: 80%;
    margin: 0 auto;
  }
}
</style>
