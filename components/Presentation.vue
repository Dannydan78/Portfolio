<template>
  <div class="main mt-10 border rounded-md" id="presentation">
    <h2 class="ml-5 text-white font-bold">PRESENTATION</h2>
    <div class="line h-px ml-10 mr-10"></div>
    <div class="container text-white mt-8 rounded-md">
      <div class="content">
        <div class="flex flex-col ps-3 pt-2">
          <p class="name">{{ props.Name }} {{ props.First_name }}</p>
          <p class="mt-4">
          Développeur fullstack passionné par la programmation, l'animation 3D.</p>  
          <p>Mon objectif est de combiner mon expertise en développement avec ma créativité afin des solutions innovantes et captivantes.</p>
          <p>Mon expérience dans le développement ainsi que ma passion pour l'animation m'a conduit sur <span class="three font-bold">Three.js</span>.</p>
          <button @click="initBigRectangle" class="button">En savoir plus</button>
        </div>
        <div v-show="showAnimation" class="hero-figure-box-05">
          <img src="/images/lar.png" class="" alt="">
        </div>
      </div>
    </div>
    <transition name="fade-slide">
      <PicturesSlide v-if="showPicturesSlide" />
    </transition>
  </div>
</template>



<script setup>
import { defineProps, ref, watch } from 'vue';
import anime from 'animejs/lib/anime.es.js';

const props = defineProps({
  Name: {
    type: String,
    default: "DARRAGON-KONKI"
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
const showPicturesSlide = ref(false);
const showMyStack = ref(false);

const initBigRectangle = () => {
  showAnimation.value = true;

  anime.timeline({
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
    })
    .add({
      duration: 1,
      complete: () => {
        showMyStack.value = true;
      }
    });
};
watch(showMyStack, (newValue) => {
  if (newValue) {
    showPicturesSlide.value = true;
  }
});

</script>

<style scoped>
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

.hero-figure-box-05 {
  width: 200px;
  height: 200px;
  /* taille en fonction de votre animation */
  /* background-color: rgba(0, 0, 0, 0.8);
    border-radius: 10px; */
  display: flex;
  align-items: center;
  justify-content: center;
  transform-origin: center;
  /* perspective: 500px; */
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
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  /* Espacement entre les colonnes */
  padding: 1rem;

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

.fade-title-enter-active,
.fade-title-leave-active {
  transition: all 2s ease-in-out;
}

.fade-title-enter-from {
  opacity: 0;

}

.fade-title-enter-to {
  opacity: 1;
}
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 4s ease-in-out;
}

.fade-slide-enter-from {
  opacity: 0;

}

.fade-slide-enter-to {
  opacity: 1;
}
.three{

  background: linear-gradient(20deg, rgb(175, 2, 214), #19f6e8);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}


</style>