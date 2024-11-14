<template>
    <main>
      <NavBar class="nav-sans-vai" />
      <Particules />
      <Intro />
      <div class="cards flex items-center justify-center px-14 ">
        <Cards />
      </div>
      <div class="presentation">
        <h1 class="titleContent font-bold">Title</h1>
      </div>
      <div data-aos="fade-up" data-aos-anchor-placement="top-bottom" class="">
        <Presentation />
      </div>
      <div class="presentation">
        <h1 class="titleContent font-bold">Title</h1>
      </div>
      <Experience />
    </main>
  </template>
  
  <script setup>
  import { onMounted } from "vue";
  import AOS from "aos";
  import "aos/dist/aos.css";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  
  onMounted(() => {
  
    AOS.init({
      duration: 1500, 
      once: true, // `true`, l'animation ne se reproduira pas lors de nouveaux scrolls
      offset: 100, // Décalage avant que l'élément soit visible
    });
  
 
  });
  </script>
  
  <style scoped>
  @import url("https://fonts.cdnfonts.com/css/red-hat");
  
  main {
    font-family: "Red Hat Display", sans-serif;
    
  }
  
  .cards {
    margin-top: 11rem;
  }
  
  .slide {
    padding-top: 11rem;
  }
  .presentation{
    margin-top: 10rem;
  }
  .titleContent {
    font-size: 2rem ;
    text-align: center;
    color: aliceblue;
    
  }
  </style>
  