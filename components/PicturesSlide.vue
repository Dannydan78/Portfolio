<template>
  <div class="staggering-grid-demo">
    <div class="el" v-for="(icon, index) in icons" :key="index">
      <img :src="icon.src" :alt="icon.alt">
    </div>
  </div>
</template>

<script>
import anime from 'animejs/lib/anime.es.js'; // Assure-toi que anime.js est importé

export default {
  data() {
    return {
      // Liste des SVGs ou icônes à afficher
      icons: [
        { src: 'images/png-transparent-vuejs-original-logo-icon.png', alt: 'icon1' },
        { src: 'images/city.avif', alt: 'icon2' },
        { src: 'images/city.avif', alt: 'icon3' },
        // Ajoute d'autres icônes ici
      ]
    };
  },
  mounted() {
    this.animateGrid();
    this.addHoverEffect();
  },
  methods: {
    // Animer la grille au chargement
    animateGrid() {
      anime({
        targets: '.staggering-grid-demo .el',
        scale: [
          { value: 0.1, easing: 'easeOutSine', duration: 500 },
          { value: 1, easing: 'easeInOutQuad', duration: 1200 }
        ],
        delay: anime.stagger(200, { grid: [14, 5], from: 'center' }),
        loop: true,
        direction: 'alternate',  // Alterne entre les deux états de l'animation (vers 0.1 et 1)
        easing: 'easeInOutQuad',
      });
    },
    // Ajouter un effet de survol pour chaque élément
    addHoverEffect() {
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
            scale: 1, // Retour à la taille d'origine
            easing: 'easeInOutQuad',
            duration: 300
          });
        });
      });
    }
  }
};
</script>

<style scoped>
.staggering-grid-demo {
  display: grid;
  grid-template-columns: repeat(14, 1fr); /* Nombre de colonnes, ajuste selon ton besoin */
  gap: 10px; /* Espacement entre les éléments */
  padding: 20px;
}

.staggering-grid-demo .el {
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 0.3s ease-in-out;
}

.staggering-grid-demo img {
  max-width: 100%;
  transition: transform 0.3s ease-in-out;
}
</style>
