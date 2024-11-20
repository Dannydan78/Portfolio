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
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>     
        </div>
        <div class="text-white mt-10 text-2xl text-center">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum eveniet delectus, tempora similique laudantium aliquam itaque eum modi. Quisquam hic minus dicta necessitatibus voluptas accusantium quas, ipsam ex repellat laborum.</div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const container = ref(null);
const blurAmount = ref(8); // Valeur initiale du blur
const scale = ref(1.2); // Scale initial (120%)

const handleScroll = () => {
    const element = container.value;
    if (!element) return;

    const rect = element.getBoundingClientRect();
    const viewportHeight = window.innerHeight;
    
    // Calculer la position relative de l'élément par rapport à la fenêtre
    const distanceFromTop = rect.top;
    const elementVisible = viewportHeight - distanceFromTop;
    
    // Calculer le pourcentage de visibilité (0 à 1)
    const visibilityRatio = Math.min(Math.max(elementVisible / viewportHeight, 0), 1);
    
    // Appliquer le blur inversement proportionnel à la visibilité
    blurAmount.value = 15 * (1 - visibilityRatio);
    
    // Ajuster la scale de 1.2 à 1
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
    { image: "images/passions/naruto.jpg" }
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
    { image: "images/passions/boxe.jpg" },
]);


</script>

<style scoped>
.passion-container {
    width: 100%;
    transition: all 0.3s ease-out;
    transform-origin: center;
    will-change: transform, filter; 
    perspective: 1000px; 
    margin-top: 6rem;

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
    margin-top: 100px; /* Décalage vers le bas */
}

.column-large {
    max-width: 400px;
    margin-top: ; /* Cette colonne commence plus haut */
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