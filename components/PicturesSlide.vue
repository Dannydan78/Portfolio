<template>
  <div class="staggering-grid">
    <!-- Utilisation de v-for pour afficher les icônes -->
    <div v-for="(icon, index) in icons" :key="index" class="el">
      <img :src="icon.src" :alt="icon.alt" />
    </div>
  </div>
</template>


<script setup>
import { ref, onMounted } from 'vue';
import anime from 'animejs/lib/anime.es.js'; 


const icons = ref([
  { src: 'icons/Php.svg', alt: 'icon1' },
  { src: 'icons/Laravel.svg', alt: 'icon2' },
  { src: 'icons/Javascript.svg', alt: 'icon3' },
  { src: 'icons/Vue.svg', alt: 'icon4' },
  { src: 'icons/Nuxt.svg', alt: 'icon5' },
]);

// Fonction pour animer la grille
function animateGrid() {
  anime({
    targets: '.staggering-grid .el',
    // delay: anime.stagger(200, { grid: [14, 5], from: 'center' }),
  translateX: 250,
  autoplay: true,
  easing: 'easeInOutSine'
  });
}

// Fonction pour ajouter les effets de survol
function addHoverEffect() {
  const gridItems = document.querySelectorAll('.staggering-grid-demo .el');

  gridItems.forEach(item => {
    item.addEventListener('mouseover', () => {
      anime({
        targets: item,
        scale: 1.2, // Zoom sur l'élément au survol
        easing: 'easeInOutQuad',
        duration: 300
      });
    });

    item.addEventListener('mouseout', () => {
      anime({
        targets: item,
        // scale: 1, // Retour à la taille d'origine
        easing: 'easeInOutQuad',
        duration: 300
      });
    });
  });
}

// Appeler les fonctions une fois le composant monté
onMounted(() => {
  animateGrid();
  addHoverEffect();
});
</script>



<style scoped>
.staggering-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr); /* Nombre de colonnes, ajuste selon ton besoin */
  /* gap: 20px; Espacement entre les éléments */
  /* padding: 20px;       */
}

.staggering-grid .el {
  display: flex;
  justify-content: center;
  align-items: center;
  /* transition: transform 0.3s ease-in-out; */
}

.staggering-grid img {
  max-width: 80%; /* Réduit la taille des icônes */
  max-height: 50%;
  /* object-fit: contain;  */
  /* transition: transform 0.3s ease-in-out; */
}
</style>
