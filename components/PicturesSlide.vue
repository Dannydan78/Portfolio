<template>
  <div>
    <h3 class="stack ml-8 text-purple-300">Maîtrise des technos</h3>
    <div class="flex flex-col w-1/2">
      <p class="mt-4 ml-8 text-white">
        En backend, maîtrise de <span class="three font-bold">PHP</span> et le framework<span class="three font-bold"> Laravel</span>, pour la gestion de base de données, des API.</p>
       <p class="mt-4 ml-8 text-white">Pour le frontend, compétences en JavaScript avec les frameworks <span class="three font-bold">Vue.js</span> et <span class="three font-bold">Nuxt.js</span>.</p>
   
      <p class="mt-4 ml-8 text-white">
        Ma passion pour le métier m'a conduit sur <span class="three font-bold">Three.js</span>.</p> 
        <p class="mt-4 ml-8 text-white"><span class="three font-bold">Three.js</span>, <span class="three font-bold">GSAP</span> et <span class="three font-bold">Anime.js</span> utilisés pour les animations de mon portfolio.</p>
   
    </div>
  <div class="staggering-grid">
    <div v-for="(icon, index) in icons" :key="index" class="el">
      <img :src="icon.src" :alt="icon.alt" />
    </div>
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


function animateGrid() {
  anime({
    targets: '.staggering-grid .el',
    delay: anime.stagger(100, { grid: [14, 5], from: 'center' }),
  // translateX: 20,
  // scale:1.09,
  autoplay: true,
  easing: 'easeInOutSine',
  direction: 'alternate',
  // loop:true,
  });
}

onMounted(() => {
  animateGrid();

});
</script>



<style scoped>
.staggering-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  /* gap: 20px; */
  /* padding: 20px;       */
}

.staggering-grid .el {
  display: flex;
  justify-content: center;
  align-items: center;
  /* transition: transform 0.3s ease-in-out; */
}

.staggering-grid img {
  max-width: 80%; /* Réduit la taille  */
  max-height: 50%;
  /* object-fit: contain;  */
  /* transition: transform 0.3s ease-in-out; */
}

.stack {
  font-size: 30px;
  /* background: linear-gradient(20deg, rgb(175, 2, 214), #19f6e8);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block; */
  
}

.three{

background: linear-gradient(20deg, rgb(175, 2, 214), #19f6e8);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}


</style>
