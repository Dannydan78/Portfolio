<template>
  <div class="main mt-10 border border-gray-500 rounded-md" id="presentation">
    <h2 class="ml-5 text-white font-bold mt-5">PRESENTATION</h2>
    <div class="line h-px ml-10 mr-10"></div>
    <div class="container text-white mt-8 rounded-md">
      <div class="content">
        <div class="flex flex-col ps-3 pt-2">
          <p class="name text-purple-300">{{ props.Name }} {{ props.First_name }}</p>
          <p class="mt-4">
          Développeur fullstack passionné par la programmation, l'animation 3D, curieux et à la fois créatif mon objectif est de créer des expériences qui vont au delà de la simple fonctionnalité.</p>  
          <p>Pour moi, la programmation est un jeu où seules l'imagination et la créativité fixent les limites.</p>
          <p>Chaque défi résolu en cache un autre il y a toujours de nouvelles portes qui s'ouvrent, même quand on pense être arrivé a la fin."</p>
          <button @click="initBigRectangle" class="button">En savoir plus</button>
        </div>
        <div v-show="showAnimation" class="hero-figure-box-05">
          <img src="/images/photo-danny.jpg" class="" alt="">
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
    margin-left: 1rem;
    margin-right: 1rem;
    background-image: linear-gradient(100deg, rgb(9, 14, 2), rgba(138, 43, 226, 0.6));
}

.container {
    display: flex;
    flex-direction: column;
    margin-inline: auto;
    border-radius: 5px;
    min-height: 300px;
    margin-bottom: 3rem;
}

.content {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
    padding: 1rem;
}

h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
}

.name {
    font-size: 24px;
}

.button {
    padding: 10px 20px;
    margin-left: 2rem;
    margin-top: 1rem;

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
    max-width: 200px;
}

.button:hover {
  transition: all 0.5s ease-out;
  box-shadow:
    0 4px 20px rgba(184, 5, 204, 0.4),
    0 0 40px rgba(85, 2, 227, 0.6),
    0 0 60px rgba(10, 130, 191, 0.7);
}

.hero-figure-box-05 {
    width: 100%;
    height: auto;
    display: flex;
    align-items: center;
    justify-content: center;
}

.hero-figure-box-05 img {
    width: 100%;
    max-width: 300px;
    height: auto;
    border-radius: 10px;
}


@media screen and (min-width: 768px) {
    .main {
        margin-left: 5rem;
        margin-right: 5rem;
    }

    .content {
        grid-template-columns: 1fr 1fr;
    }

    .name {
        font-size: 28px;
    }
}

@media screen and (min-width: 1024px) {
    .main {
        margin-left: 15rem;
        margin-right: 15rem;
    }

    .content {
        gap: 40px;
    }

    .name {
        font-size: 30px;
    }

    .button {
        margin-top: 6rem;
    }
}

@media screen and (min-width: 1536px) {
    .main {
        margin-left: 20rem;
        margin-right: 20rem;
    }
}


@media screen and (max-width: 480px) {
    .main {
        margin-left: 0.5rem;
        margin-right: 0.5rem;
    }

    .name {
        font-size: 22px;
    }

    .button {
        margin-top: 1rem;
    }

    .hero-figure-box-05 img {
        max-width: 250px;
    }
}

.svg {
  justify-content: center;
  align-items: center;
}

.line {
  background: white;
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