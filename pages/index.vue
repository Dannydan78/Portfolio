<template>
    <main class="min-h-screen flex flex-col">
      <NavBar ref="navbarRef" class="nav-sans-vai" />
      <Particules />
      <Intro />
      <div class="cards flex items-center justify-center px-14 ">
        <Cards :scrollToSection="navbarRef?.scrollToSection" />
      </div>
      <!-- <div data-aos="fade-up" data-aos-anchor-placement="top-bottom" class=""> -->
      <div class="presentation">
        <p class="exp">Qui suis-je?</p>
        <h1 class="titleContent font-bold">Un parcours, une vision, une passion</h1>
        <p class="text-gray-400 text-justify">"Ce que tu fais ne détermine pas qui tu es, mais ce que tu cherches à devenir révèle ta véritable nature."</p>
      <!-- </div> -->
        <Presentation />
      </div>
      <!-- <div data-aos="fade-right" data-aos-anchor-placement="top-bottom" class=""> -->
      <div class="presentation">
        <p class="exp">EXP</p>
        <h1 class="titleContent font-bold">Title Lorem, ipsum dolor sit amet consectetur.</h1>
        <p class="text-gray-400 text-justify">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo obcaecati fugiat libero tempora quo? Corrupti</p>
      <!-- </div> -->
      <Experience />
      </div>
      <div class="presentation pt-8">
        <p class="exp">Passions</p>
        <h1 class="titleContent font-bold">Title Lorem, ipsum dolor sit amet consectetur.</h1>
        <p class="text-gray-400 text-justify pb-2">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Explicabo obcaecati fugiat libero tempora quo? Corrupti</p>
      </div>
      <Passion />
      <!-- <div data-aos="fade-up" data-aos-anchor-placement="top-bottom" class=""> -->
      <div class="pt-16">
        <Contact :identity="identityData" />
    </div>
    <!-- </div> -->
    <div class="footer mt-6">
      <Footer 
        :identity="identityData" 
        :scroll-to-section="navbarRef?.scrollToSection"
      />
    </div>
    </main>
  </template>
  
  <script setup>
  import { onMounted, ref } from "vue";
  import AOS from "aos";
  import "aos/dist/aos.css";
  
  const identityData = ref({
    last_name: "Darragon-Konki",
    first_name: "Danny",
    job: "Développeur web fullstack",
    email: "danny.darragon.konki@gmail.com",
    github: "https://github.com/Dannydan78",
    linkedin: "https://www.linkedin.com/in/danny-darragon-konki-98ab0226b/",
  })
  
  const updateIdentity = (data) => {
    identityData.value = data;
  };
  
  const navbarRef = ref(null);
  
  onMounted(() => {
  
    AOS.init({
      duration: 1500, 
      once: true, // `true`, l'animation ne se reproduira pas lors de nouveaux scrolls
      offset: 100, // Décalage avant que l'élément soit visible
    });
  
    // Vérifier que la fonction est disponible
    console.log('Navbar scroll function:', navbarRef.value?.scrollToSection);
  });
  </script>
  
  <style scoped>
  @import url("https://fonts.cdnfonts.com/css/red-hat");
  
  main {
    font-family: "Red Hat Display", sans-serif;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
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
    font-size: 20px;
  }

  .footer{
    margin-top: 5rem;
  }
  </style>
  