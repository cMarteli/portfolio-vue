<template>
  <section id="about" class="section alternate-bg">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-grid">
        <div class="about-text">
          <p>
            Fullstack developer based in Western Australia.
          </p>
          <p>
            Leveraging 10+ years of background in the gaming and mining industries with a passion for technology to build robust software solutions.
          </p>
        </div>
        <div class="about-visual">
          <div class="profile-picture-container">
            <img
              src="@/assets/images/portrait.jpg"
              alt="Portrait photo of Vic"
              class="profile-picture"
            />
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

/* --- About --- */
.about-grid {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: 4rem;
  align-items: center;
}

.profile-picture-container {
  width: 100%;
  aspect-ratio: 1/1;
  border-radius: 10px;
  border: 2px solid #38bdf8;
  position: relative;
}

.profile-picture {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
}

.profile-picture-container::after {
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
  .profile-picture-container {
    width: 80%;
    margin: 0 auto;
  }
}
</style>
