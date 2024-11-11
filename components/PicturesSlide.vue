<template>
    <div class="scroll-container">
   <div class="scroll-content">
     <img src="/images/laravel8530.jpg" alt="Image 1" />
     <img src="/images/Vue.png" alt="Image 2" />
     <img src="/images/JavaScript-logo.png" alt="Image 3" />
     <img src="/images/php.svg" alt="Image 4" />
     <!-- Ajoutez autant d'images que nécessaire -->
   </div>
   </div>
</template>






<style scoped>
.scroll-container {
   width: 100%; /* Largeur du conteneur visible */
   height: 200px; /* Hauteur souhaitée du conteneur */
   overflow: hidden; /* Cache les éléments débordants */
   /* position: absolute; */
   color: bisque;
   justify-content: center;
   justify-items: center;
   align-items: center;
  
 }

 .scroll-content {
   display: flex;
   flex-direction: row;
   animation: scroll-horizontal 10s linear infinite; /* Durée et répétition */
 }

 .scroll-content img {
   width: 200px; /* Largeur des images */
   height: auto;
   margin-right: 10px; /* Espacement entre les images */
 }

 @keyframes scroll-horizontal {
   0% {
     transform: translateX(0);
   }
   100% {
     transform: translateX(-100%);
   }
 }

</style>
