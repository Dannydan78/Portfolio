<template>
  <div class="main mt-10 rounded-md" id="presentation">
    <div class="flex flex-row gap-4">
      <div class="card flex flex-col w-1/2 border rounded-md">
        <h2 class="ml-5 text-white font-bold">EXPERIENCE</h2>
        <div class="ml-8 text-gray-400">Lorem ipsum, dolor sit amet consectetur adipisicing elit.</div>
        <div class="ml-8 text-gray-400">Lorem ipsum, dolor sit amet</div>
        <div class="m-4 text-white mt-8 rounded-md scroll-container">
          <div class="scroll-content flex flex-col">
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
            <div class="flex flex-row ps-3 space-x-2">
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="name">Danny</p>
              <p class="">Experience</p>
            </div>
          </div>
        </div>
      </div>
      <!-- Deuxième card -->
      <div class="card2 border w-1/2 rounded-md">
      </div>
    </div>

    <transition name="fade-slide">
      <PicturesSlide v-if="showPicturesSlide" />
    </transition>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';

const startAutoScroll = () => {
  const container = document.querySelector('.scroll-container');
  const content = document.querySelector('.scroll-content');
  
  if (!container || !content) return;

  let scrollInterval;
  let isPaused = false;
  let direction = 1; // 1 pour descendre, -1 pour monter
  let scrollSpeed = 1; // Vitesse de défilement

  const scroll = () => {
    if (!isPaused) {
      container.scrollTop += scrollSpeed * direction;
      
      // Changement de direction en bas
      if (container.scrollTop + container.clientHeight >= content.scrollHeight) {
        direction = -1;
      }
      // Changement de direction en haut
      if (container.scrollTop <= 0) {
        direction = 1;
      }
    }
  };

  // Gestion de la pause au survol
  const handleMouseEnter = () => isPaused = true;
  const handleMouseLeave = () => isPaused = false;

  container.addEventListener('mouseenter', handleMouseEnter);
  container.addEventListener('mouseleave', handleMouseLeave);

  scrollInterval = setInterval(scroll, 50);

  // Nettoyage
  onBeforeUnmount(() => {
    if (scrollInterval) {
      clearInterval(scrollInterval);
    }
    container.removeEventListener('mouseenter', handleMouseEnter);
    container.removeEventListener('mouseleave', handleMouseLeave);
  });
};

onMounted(() => {
  startAutoScroll();
});
</script>

<style scoped>
.scroll-container {
  max-height: 100px;
  overflow-y: hidden;
  position: relative;
  mask-image: linear-gradient(
    to bottom,
    transparent 0%,
    black 20%,
    black 80%,
    transparent 100%
  );
  -webkit-mask-image: linear-gradient(
    to bottom,
    transparent 0%,
    black 20%,
    black 80%,
    transparent 100%
  );
  transition: scroll-top 0.3s ease-in-out; /* Ajout d'une transition douce */
}

.scroll-content {
  padding: 20px 0;
  transition: transform 0.3s ease-in-out; /* Ajout d'une transition douce */
}

.main {
  margin-left: 15rem;
  margin-right: 15rem;
  color: white;
}

h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
}

.card {
  background-image: linear-gradient(100deg, rgb(9, 14, 2), rgba(45, 5, 245, 0.7));
  min-height: 400px;
}

.card2 {
  background-image: linear-gradient(1000deg, rgb(9, 14, 2), rgba(45, 5, 245, 0.7));
}

.line {
  background: white;
}

/* Animation pour le défilement */
@keyframes autoScroll {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(-100%);
  }
}

/* Optionnel : Style pour les éléments "name" */
.name {
  transition: color 0.3s ease;
}

.name:hover {
  color: #19f6e8;
}
</style>