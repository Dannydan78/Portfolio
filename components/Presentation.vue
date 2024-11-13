<template>
  <div class="main mt-10 border rounded-md">
    <h2 class="ml-5 text-white font-bold">PRESENTATION</h2>
    <div class="line h-px ml-10 mr-10"></div>
    <div class="container text-white mt-8 rounded-md">
      <div class="content">
        <div class="flex flex-col ps-3 pt-2">
          <p class="name">{{ props.Name }}</p>
          <p class="name">{{ props.First_name }}</p>
          <p>
            Développeur web fullstack passion Lorem ipsum dolor sit, amet consectetur adipisicing elit.
            Magnam quibusdam rem a, eaque molestiae iusto adipisci non, deserunt dignissimos molestias quasi.
            Labore, ut cum accusamus vitae minus impedit mollitia aut.
          </p>
          <button @click="initBigRectangle" class="button">Click !</button>
        </div>


        <div v-show="showAnimation" class="hero-figure-box-05">
          <img src="/images/lar.png" class="" alt="">
        </div>
      </div>
    </div>
    <PicturesSlide />
  </div>
</template>



<script setup>
import { defineProps, ref } from 'vue';
import anime from 'animejs/lib/anime.es.js'; // Assurez-vous que l'importation d'animejs est correcte

const props = defineProps({
  Name: {
    type: String,
    default: "Darragon-Konki"
  },
  First_name: {
    type: String,
    default: "Danny"
  },
  Date_of_birth: {
    type: String,
    default: "13 juillet 1990"
  }
});

const showAnimation = ref(false);

const initBigRectangle = () => {
  // Rendre l'élément visible en activant showAnimation
  showAnimation.value = true;

  // Créez l'animation au moment du clic
  bigDarkRectangle = anime.timeline({
    targets: '.hero-figure-box-05',
    duration: 400,
    easing: 'easeInOutExpo',
    autoplay: true,
  })
    .add({
      scaleX: [0.05, 0.05],
      scaleY: [0, 1],
    })
    .add({
      scaleX: 1
    })
    .add({
      duration: 800,
      rotateY: '-360deg',
      rotateX: '8deg',

    });
};
</script>

<style scoped>
.hero-figure-box-05 {
  width: 200px;
  /* ou toute autre taille nécessaire */
  height: 200px;
  /* taille en fonction de votre animation */
  /* background-color: rgba(0, 0, 0, 0.8);
    border-radius: 10px; */
  display: flex;
  /* ou tout autre style que vous préférez */
  align-items: center;
  justify-content: center;
  transform-origin: center;
  /* pour l'animation de rotation */
  /* perspective: 500px; utile si vous souhaitez des effets 3D */
  transition: all 0.5s ease-in-out;
  /* transition pour les transformations */
}
.svg {
  justify-content: center;
  align-items: center;
}

.container {
  display: flex;
  flex-direction: column;
  margin-inline: auto;
  border-radius: 5px;
  /* min-height: 400px; */
  margin-bottom: 5rem;
}

h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
  /* color: var(--title-color); */
}

.content {
  display: grid;
  /* Utilisation de la grille pour les colonnes */
  grid-template-columns: 1fr 1fr;
  /* Deux colonnes égales */
  gap: 20px;
  /* Espacement entre les colonnes */
  padding: 1rem;

}

.main {
  margin-left: 15rem;
  margin-right: 15rem;
  background-image: url('images/fade.jpg');
  background-image: linear-gradient(100deg, rgb(9, 14, 2), rgba(138, 43, 226, 1));
  /* background-size: cover;  L'image couvre toute la zone de l'élément  */
  background-position: center;
  /* L'image est centrée */
  background-repeat: no-repeat;

}

.button {
  padding: 10px 20px;
  margin-top: 8rem;
  font-size: 16px;
  background-color: rgba(138, 43, 226, 0.7);
  border: none;
  border-radius: 25px;
  cursor: pointer;
  box-shadow:
    0 4px 15px rgba(175, 2, 214, 0.6),
    0 0 30px rgba(175, 2, 214, 0.6);
  transition: box-shadow 0.3s ease, transform 0.3s ease;
  width: auto;
  /* Ajuste la largeur du bouton */
  max-width: 200px;
  /* Limite la largeur maximale du bouton */
  margin: 0 auto;
  /* Centre le bouton */
}


.button:hover {
  transition: all 0.5s ease-out;
  box-shadow:
    0 4px 20px rgba(184, 5, 204, 0.4),
    0 0 40px rgba(85, 2, 227, 0.6),
    0 0 60px rgba(10, 130, 191, 0.7);

}

.line {
  /* background: #19f6e8; */
  background: white;
}

.name {
  font-size: 30px;
  background: linear-gradient(20deg, rgb(175, 2, 214), #19f6e8);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

img {
  border-radius: 10px;
}
</style>