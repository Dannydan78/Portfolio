<template>
    <div class="main mt-10 border rounded-md">
    <h2 class="ml-5 text-white">Présentation</h2>
    <div class="line h-px bg-gradient-to-r from-gray-100 to-blue-500 ml-10 mr-10"></div>

    <div class="container text-white mt-8 rounded-md">
      <div class="content">
        <div class="flex flex-col ps-3 pt-2">
        <p class="">Nom : {{ props.Name }}</p>
        <p class="">Prénom : {{ props.First_name }}</p>
        <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Magnam
            quibusdam rem a, eaque molestiae iusto adipisci non, deserunt dignissimos
            molestias quasi. Labore, ut cum accusamus vitae minus impedit mollitia aut.
        </p>
        <button class="button m-8">En savoir plus</button>
    </div>
       <img src="/images/lar.png" alt="">
          
           
       </div>
    </div>
</div>
  </template>
  
<script setup>
import { defineProps } from 'vue';

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

</script>
  
  <style scoped>
  .container {
    /* margin: 10rem; */
    display: flex;
    flex-direction: column;
    margin-inline: auto;
    border-radius: 5px;
    /* background: rgba(79, 80, 80, 0.4); */
    min-height: 400px;
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
    display: grid;  /* Utilisation de la grille pour les colonnes */
    grid-template-columns: 1fr 1fr;  /* Deux colonnes égales */
    gap: 20px;  /* Espacement entre les colonnes */
    padding: 1rem;  /* Padding interne */

  }

  .main {
  margin-top: 15rem;
  background-image: url('images/fade.jpg');
  background-image: linear-gradient(100deg, rgb(9, 14, 2), rgba(138, 43, 226, 1));
  /* background-size: cover;  L'image couvre toute la zone de l'élément  */
  background-position: center; /* L'image est centrée */
  background-repeat: no-repeat; 

}

.button {
    padding: 10px 20px;
    margin-top: 10rem;
    font-size: 16px;
    font-weight: bold;
    color: rgb(35, 34, 34);
    background-color: #dcd7d7;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    box-shadow:
        0 4px 15px rgba(175, 2, 214, 0.6),
        0 0 30px rgba(175, 2, 214, 0.6);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
    width: auto; /* Ajuste la largeur du bouton */
    max-width: 200px; /* Limite la largeur maximale du bouton */
    margin: 0 auto; /* Centre le bouton */
}


.button:hover {
    box-shadow:
        0 4px 20px rgba(184, 5, 204, 0.4),
        0 0 40px rgba(85, 2, 227, 0.6),
        0 0 60px rgba(10, 130, 191, 0.7);
    transform: scale(1.05);
}
  
  </style>
  