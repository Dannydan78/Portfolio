<template>
   <div class="main mt-10 border rounded-md" id="presentation">
    <h2 class="ml-5 text-white font-bold">EXPERIENCE</h2>
    <div class="line h-px ml-10 mr-10"></div>
    <div class="container text-white mt-8 rounded-md">
      <div class="content">
        <div class="flex flex-col ps-3 pt-2">
          <p class="name"></p>
          <p class="mt-4 mb-4">
          Développeur fullstack passionné par la programmation, l'animation 3D. Mon expérience dans le développement ainsi que ma passion pour l'animation m'a conduit sur <span class="three font-bold">Three.js</span>. Mon objectif est de combiner mon expertise en développement avec ma créativité afin des solutions innovantes et captivantes.
          </p>
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

</script>

<style scoped>
    .main {
  margin-left: 15rem;
  margin-right: 15rem;
  background-image: url('images/fade.jpg');
  background-image: linear-gradient(100deg, rgb(9, 14, 2), #19f6e8);
  /* background-size: cover;  L'image couvre toute la zone de l'élément  */
  background-position: center;
  /* L'image est centrée */
  background-repeat: no-repeat;
}





h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
  /* color: var(--title-color); */
}





.line {
  /* background: #19f6e8; */
  background: white;
}





</style>