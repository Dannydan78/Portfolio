<template>
    <main>
      <NavBar class="nav-sans-vai" />
      <Particules />
      <Intro />
      <div class="cards flex items-center justify-center px-14 ">
        <Cards />
      </div>
      <div data-aos="fade-up" data-aos-anchor-placement="top-bottom" class="">
      <div class="presentation">
        <p class="exp">Qui suis-je?</p>
        <h1 class="titleContent font-bold">Title Lorem, ipsum dolor sit amet consectetur.</h1>
        <p class="text-gray-400 text-justify">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo obcaecati fugiat libero tempora quo? Corrupti</p>
      </div>
        <Presentation />
      </div>
      <div data-aos="fade-right" data-aos-anchor-placement="top-bottom" class="">
      <div class="presentation">
        <p class="exp">EXP</p>
        <h1 class="titleContent font-bold">Title Lorem, ipsum dolor sit amet consectetur.</h1>
        <p class="text-gray-400 text-justify">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo obcaecati fugiat libero tempora quo? Corrupti</p>
      </div>
      <Experience />
      </div>
      <div class="presentation">
        <p class="exp">Passion</p>
        <h1 class="titleContent font-bold">Title Lorem, ipsum dolor sit amet consectetur.</h1>
        <p class="text-gray-400 text-justify">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo obcaecati fugiat libero tempora quo? Corrupti</p>
      </div>
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
  p{
    text-align: center;
  }

  .exp{
    background: linear-gradient(20deg, rgb(175, 2, 214), #19f6e8);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  }
  </style>
  