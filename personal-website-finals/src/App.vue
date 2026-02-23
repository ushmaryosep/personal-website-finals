<template>
  <div class="hero-container">
    <img 
      src="https://github.com/ushmaryosep/personal-website-finals/blob/main/live%20background.gif?raw=true" 
      class="hero-bg"
      alt="Grand Line"
    />
    <div class="overlay"></div>

    <div class="stage" :class="{ 'is-shifted': showPoster }">
      
      <section class="branding-section">
        <div class="content-box">
          <img 
            src="https://raw.githubusercontent.com/ushmaryosep/personal-website-finals/refs/heads/main/hero%20title.png" 
            class="hero-title-img"
            alt="Joshmar Clavero"
          />

          <p class="pirate-description">
            Ahoy, wanderer of the seas! This be the personal stronghold of Joshmar Clavero, 
            where all tales of the captain be gathered — from humble beginnings and 
            Grand Line training, to battle skills, crew pastimes, glorious achievements, 
            and ways to send a raven across the seas. Enter, and learn what makes 
            this pirate's legend grow.
          </p>

          <button @click="showPoster = true" class="pirate-btn">
            VIEW WANTED POSTER ☠
          </button>
        </div>
      </section>

      <section class="poster-section">
        <div class="poster-content">
          <img 
            src="https://raw.githubusercontent.com/ushmaryosep/personal-website-finals/refs/heads/main/HERO%20CARD.png" 
            class="hero-card-img"
            alt="Wanted Poster"
          />
          <button @click="showPoster = false" class="back-btn">
            ← BACK TO SHIP
          </button>
        </div>
      </section>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const showPoster = ref(false);
</script>

<style scoped>
.hero-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

/* Background Logic */
.hero-bg {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
  z-index: -2;
}

.overlay {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.3);
  z-index: -1;
}

/* Animation Stage Logic */
.stage {
  display: flex;
  width: 200vw; /* Holds both sections side-by-side */
  height: 100vh;
  transition: transform 1.2s cubic-bezier(0.65, 0, 0.35, 1); /* Morphing effect */
}

.is-shifted {
  transform: translateX(-100vw);
}

.branding-section, .poster-section {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5%;
}

/* --- SECTION A ANIMATIONS --- */

.hero-title-img {
  width: 100%;
  max-width: 700px;
  /* LOOPING ZOOM ANIMATION */
  animation: titleZoom 5s ease-in-out infinite;
  filter: drop-shadow(0 0 15px rgba(255, 255, 255, 0.2));
}

@keyframes titleZoom {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

.pirate-description {
  color: white;
  font-size: 1.2rem;
  max-width: 650px;
  margin: 30px auto;
  text-shadow: 2px 2px 10px rgba(0,0,0,0.8);
  /* LOOPING PULSE ANIMATION */
  animation: descriptionPulse 3s ease-in-out infinite;
}

@keyframes descriptionPulse {
  0%, 100% { opacity: 0.8; transform: translateY(0); }
  50% { opacity: 1; transform: translateY(-8px); }
}

/* --- BUTTON STYLES & HOVER --- */

.pirate-btn {
  background: #f4d03f;
  color: #1a1a1a;
  border: 4px solid #5d4037;
  padding: 15px 40px;
  font-weight: 900;
  font-size: 1.2rem;
  cursor: pointer;
  transition: 0.3s;
  box-shadow: 0 5px 15px rgba(0,0,0,0.4);
}

.pirate-btn:hover {
  background: #fff;
  transform: scale(1.1) rotate(-2deg);
  box-shadow: 0 0 25px rgba(255, 208, 0, 0.6);
}

/* --- SECTION B (WANTED POSTER) --- */

.hero-card-img {
  max-height: 85vh;
  max-width: 90%;
  border: 8px solid #333;
  box-shadow: 0 0 60px rgba(0,0,0,0.9);
}

.back-btn {
  display: block;
  margin: 20px auto;
  background: transparent;
  color: white;
  border: 1px solid white;
  padding: 8px 16px;
  cursor: pointer;
  opacity: 0.7;
}

.back-btn:hover { opacity: 1; }

/* Responsive adjustments */
@media (max-width: 768px) {
  .hero-title-img { max-width: 90%; }
  .pirate-description { font-size: 1rem; }
}
</style>