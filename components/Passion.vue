<template>
    <div class="passion-container" id="passions" ref="container" :style="{
        filter: `blur(${blurAmount}px)`,
        transform: `scale(${scale})`,
    }">
        <div class="flex flex-row justify-center gap-4">
            <div class="cards-column">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-column column-large">
                <article class="card border border-gray-500" v-for="(item, index) in cards3D" :key="index">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-column">
                <article class="card border border-gray-500" v-for="(item, index) in cardsGame" :key="index">
                    <figure>
                        <img :src="item.image" alt="Image" />ff
                    </figure>
                </article>
            </div>     
        </div>
        <div class="passion-outro text-center pt-10">
    <h1 class="titleContent font-bold text-white mb-4">
        <span class="text-purple-500">&lt;</span> 
        DÉVELOPPEUR LE JOUR 
        <span class="text-purple-500">/&gt;</span>
    </h1>
    
    <div class="passion-list text-gray-400 flex flex-wrap justify-center gap-3 px-4">
        <span class="passion-tag">GAMER</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">MANGAKA SPIRIT</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">3D PASSIONATE</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">BLENDER ADDICT</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">DATA EXPLORER</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">ANIME LOVER</span>
        <span class="text-purple-500">•</span>
        <span class="passion-tag">BOXEUR</span>
    </div>
    <p class="text-gray-400 max-w-2xl mx-auto mt-6 px-4">
        <span class="text-purple-500">&lt;</span> 
        Chaque passion est une ligne de code sur le chemin de ma créativité 
        <span class="text-purple-500">/&gt;</span>
    </p>
    <p class="text-sm text-gray-500 max-w-2xl mx-auto mt-2 px-4">
        Du ring de boxe à la modélisation 3D, en passant par l'univers des mangas, 
        tout ce que mes yeux aperçoivent enrichit ma façon de coder et de créer
    </p>
</div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';


const container = ref(null);
const blurAmount = ref(8); // Blur
const scale = ref(1.2); 

const handleScroll = () => {
    const element = container.value;
    if (!element) return;

    const rect = element.getBoundingClientRect();
    const viewportHeight = window.innerHeight;
    
  
    const distanceFromTop = rect.top;
    const elementVisible = viewportHeight - distanceFromTop;
    
  
    const visibilityRatio = Math.min(Math.max(elementVisible / viewportHeight, 0), 1);
    

    blurAmount.value = 15 * (1 - visibilityRatio);
    
  
    scale.value = 1.2 - (0.2 * visibilityRatio);
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll(); 
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});

const cards = ref([
    { image: "images/passions/rinnegan.png" },
    { image: "images/passions/naruto.jpg" },
    { image: "images/passions/naruto2.jpg" },
    { image: "images/passions/obito.jpg" }
]);
const cards3D = ref([
    { image: "images/passions/Chicken.jpg" },
    { image: "images/passions/game.png" },
    { image: "images/passions/programmation.jpg" }
]);
const cardsGame = ref([
    { image: "images/passions/Game.jpg" },
    { image: "images/passions/manette.jpg" },
    { image: "images/passions/boxe.jpg" },
    { image: "images/townAI.jpg" },
]);


</script>

<style scoped>

.passion-container {
    width: 100%;
    transition: all 0.3s ease-out;
    transform-origin: center;
    will-change: transform, filter; 
    perspective: 1000px; 
    margin-top: 3rem;

}

article {
    --img-scale: 1.001;
    --title-color: rgb(243, 239, 239);
    --link-icon-translate: -20px;
    --link-icon-opacity: 0;
    position: relative;
    border-radius: 5px;
    box-shadow: none;
    background: rgba(79, 80, 80, 0.4);
    transition: all 0.4s ease-in-out;
    overflow: hidden;
    width: 100%;
    min-height: 300px;
}

figure {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 400px;
}

article img {
    width: 100%;
    height: 100%;
    object-fit:cover;
}

.cards-column {
    display: flex;
    flex-direction: column;
    max-width: 280px;
    gap: 20px;
    margin-top: 100px; 
}

.column-large {
    max-width: 400px;
   
}

.column-large .card {
    min-height: 400px;
}

.column-large figure {
    height: 400px;
}

.card {
    min-height: 300px;
    width: 100%;
    background: rgba(79, 80, 80, 0.4);
    border-radius: 5px;
    overflow: hidden;
    transition: all 0.4s ease-in-out;
}

figure {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 300px;
}

.passion-tag {
    font-weight: 600;
    transition: all 0.3s ease;
}

.passion-tag:hover {
    color: #fff;
    transform: scale(1.1);
    cursor: default;
}

@media (max-width: 1200px) {
    .flex-row {
        flex-wrap: wrap;
        justify-content: center;
    }

    .cards-column {
        flex: 0 1 calc(50% - 2rem);
        margin-top: 20px;
    }
}

@media (max-width: 768px) {
    .flex-row {
        flex-direction: column;
        align-items: center;
    }

    .cards-column {
        max-width: 100%;
        margin-top: 20px;
    }

    .column-large {
        max-width: 100%;
    }
}
</style>