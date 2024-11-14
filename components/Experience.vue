<template>
  <div class="main mt-10 rounded-md" id="presentation">
    <div class="flex flex-row gap-4"> 
      <div class="card flex flex-col w-1/2 border rounded-md">
        <h2 class="ml-5 text-white font-bold">EXPERIENCE</h2>
        <div class="container text-white mt-8 rounded-md">
          <div class="content">
            <div class="flex flex-col ps-3 pt-2">
              <p class="name"></p>
              <p class="mt-4 mb-4">
                Développeur fullstack passionné par la programmation, l'animation 3D. Mon expérience dans le développement
                ainsi que ma passion pour l'animation m'a conduit sur <span class="three font-bold">Three.js</span>. Mon
                objectif est de combiner mon expertise en développement avec ma créativité afin de proposer des solutions
                innovantes et captivantes.
              </p>
              <button @click="initBigRectangle" class="button">En savoir plus</button>
            </div>
            <div v-show="showAnimation" class="hero-figure-box-05">
              <img src="/images/lar.png" class="" alt="">
            </div>
          </div>
        </div>
      </div>

      <!-- Deuxième card -->
      <div class="card2 border w-1/2 rounded-md"> <!-- Ajuster w-1/2 si besoin -->
        <h2 class="ml-5 text-white font-bold">EXPERIENCE</h2>
        <!-- Ajoutez du contenu ici -->
      </div>
    </div>

    <transition name="fade-slide">
      <PicturesSlide v-if="showPicturesSlide" />
    </transition>
  </div>
</template>


<script setup>

</script>

<style scoped>
.main {
  margin-left: 15rem;
  margin-right: 15rem;
}

h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
  /* color: var(--title-color); */
}

.card{
  background-image: linear-gradient(100deg, rgb(9, 14, 2), rgba(26, 29, 180, 0.7));
}
.card2{
  background-image: linear-gradient(250deg, rgb(9, 14, 2), #19f6e8);
}


.line {
  /* background: #19f6e8; */
  background: white;
}
</style>