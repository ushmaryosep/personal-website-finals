<template>
  <div class="hero-container">
    <img 
      src="https://github.com/ushmaryosep/personal-website-finals/blob/main/live%20background.gif?raw=true" 
      class="hero-bg"
      alt="Background"
    />

    <div class="stage" :class="{ 'is-shifted': showPoster }">
      
      <section class="branding-section">
        <img 
          src="https://raw.githubusercontent.com/ushmaryosep/personal-website-finals/refs/heads/main/hero%20title.png" 
          class="floating-title"
          alt="Joshmar Clavero"
        />

        <p class="pulsing-desc">
          Ahoy, wanderer of the seas! This be the personal stronghold of Joshmar Clavero, 
          where all tales of the captain be gathered — from humble beginnings and 
          Grand Line training, to battle skills, crew pastimes, glorious achievements, 
          and ways to send a raven across the seas. Enter, and learn what makes 
          this pirate's legend grow.
        </p>

        <button @click="showPoster = true" class="pirate-btn">
          <span>VIEW WANTED POSTER</span>
          <i class="skull">☠</i>
        </button>
      </section>

      <section class="poster-section">
        <div class="poster-container">
           <button class="back-btn" @click="showPoster = false">← RETURN TO SHIP</button>
           <img 
            src="https://raw.githubusercontent.com/ushmaryosep/personal-website-finals/refs/heads/main/HERO%20CARD.png" 
            class="wanted-poster-img"
          />
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
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  color: white;
}

.hero-bg {
  position: absolute;
  width: 100%; height: 100%;
  object-fit: cover;
  z-index: -1;
}

/* The Stage handles the smooth scroll/morph transition */
.stage {
  display: flex;
  width: 200vw; /* Double width to hold both sections side-by-side */
  height: 100%;
  transition: transform 0.8s cubic-bezier(0.77, 0, 0.175, 1); /* "Smooth Morph" feel */
}

.is-shifted {
  transform: translateX(-100vw); /* Moves the whole stage left */
}

.branding-section, .poster-section {
  width: 100vw;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

/* 1. LOOPING ANIMATION: Title Zoom */
.floating-title {
  width: 100%;
  max-width: 650px;
  animation: titleZoom 4s ease-in-out infinite;
}

@keyframes titleZoom {
  0%, 100% { transform: scale(1); filter: drop-shadow(0 0 10px rgba(255,215,0,0.3)); }
  50% { transform: scale(1.08); filter: drop-shadow(0 0 30px rgba(255,215,0,0.6)); }
}

/* 2. LOOPING ANIMATION: Description Pulse */
.pulsing-desc {
  max-width: 700px;
  font-size: 1.2rem;
  margin: 2rem 0;
  text-shadow: 2px 2px 8px black;
  animation: textGlow 3s infinite alternate;
}

@keyframes textGlow {
  from { opacity: 0.8; transform: translateY(0); }
  to { opacity: 1; transform: translateY(-5px); }
}

/* 3. HOVER EFFECTS: Button */
.pirate-btn {
  background: #e6c791;
  border: 4px solid #3d2b1f;
  padding: 15px 30px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.pirate-btn:hover {
  background: #f5deb3;
  transform: scale(1.1) rotate(3deg);
  box-shadow: 0 0 20px #ffcc00;
}

.pirate-btn:active {
  transform: scale(0.95);
}

/* Wanted Poster landing state */
.wanted-poster-img {
  max-height: 85vh;
  box-shadow: 0 0 50px rgba(0,0,0,0.8);
  border: 10px solid #222;
}

.back-btn {
  margin-bottom: 10px;
  background: rgba(0,0,0,0.6);
  color: gold;
  border: 1px solid gold;
  padding: 5px 15px;
  cursor: pointer;
}
</style>