<template>
    <div class="passion-container" ref="container" :style="{
        filter: `blur(${blurAmount}px)`,
        transform: `scale(${scale})`,
    }">
        <div class="flex flex-row">
            <div class="cards-container">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-container-2">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card-2': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-container">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-container-2">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card-2': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-container">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
            <div class="cards-container-2">
                <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index" :class="{ 'middle-card-2': index === 1 }">
                    <figure>
                        <img :src="item.image" alt="Image" />
                    </figure>
                </article>
            </div>
        </div>
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
    { image: "images/passions/sasuke.jpg" }
]);

</script>

<style scoped>
.passion-container {
    width: 100%;
    transition: all 0.3s ease-out;
    transform-origin: center;
    will-change: transform, filter; 
    perspective: 1000px; /* Ajoute de la profondeur à l'animation */
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
    object-fit: cover;
    transform-origin: center;
    transform: scale(var(--img-scale));
    transition: transform 0.4s ease-in-out;
}

.cards-container {
    display: flex;
    flex-direction: column;
    max-width: 350px;
    padding-inline: 24px;
    gap: 20px;
    padding-left: 0;
    margin: -10% auto;
    padding: 10% 24px;
}
.cards-container-2 {
    display: flex;
    flex-direction: column;
    max-width: 250px;
    max-height: 20px;

    gap: 20px;
    padding-left: 0;
}

.middle-card {
    min-height: 40px;
}
.middle-card-2 {
    min-height: 400px;
}

.middle-card figure {
    height: 200px;
}

@media (max-width: 968px) {
    .cards-container {
        flex-direction: column;
    }
    
    article, .middle-card {
        width: 100%;
        min-height: 40px;
    }
    
  
}

@media (max-width: 768px) {
    figure {
        height: 250px;
    }
    .passion-container {
        transform-origin: top center; /* Meilleur point d'origine sur mobile */
    }
}
</style>