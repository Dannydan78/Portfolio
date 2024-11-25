<template>
    <div class="cards-container">
        <article class="card border border-gray-500" v-for="(item, index) in cards" :key="index">
            <figure>
                <img :src="item.image" alt="Image" />
            </figure>
            <div class="article-body">
                <a @click.prevent="props.scrollToSection(item.id)">
                    <h2>{{ item.title }}</h2>
                </a>
                <p class="">{{ item.description }}</p>
                <a @click.prevent="props.scrollToSection(item.id)" class="go inline-flex items-center pt-8">
                    <svg class="icon w-3.5 h-3.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9" />
                    </svg>
                </a>
            </div>
        </article>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    scrollToSection: {
        type: Function,
        required: true
    }
});

const cards = ref([
    { 
        title: "Présentation", 
        description: "Développeur web passionné, j'aime relever des défis et créer des expériences numériques uniques.", 
        image: "images/ordinateur.avif", 
        id: "presentation" 
    },
    { 
        title: "Expérience", 
        description: "De Laravel à Vue.js, chaque projet a enrichi mon parcours de nouvelles compétences et humaines.", 
        image: "images/data.jpeg", 
        id: "experience"
    },
    { 
        title: "Passions", 
        description: "L'animation, la 3D et le jeux vidéos sont au cœur de ma créativité, pour donner vie à mes idées et à des univers immersifs.", 
        image: "images/city.avif", 
        id: "passions"
    }
]);
</script>

<style scoped>


article {
    --img-scale: 1.001;
    --title-color: rgb(243, 239, 239);
    --link-icon-translate: -20px;
    --link-icon-opacity: 0;
    position: relative;
    border-radius: 16px;
    box-shadow: none;
    background: rgba(79, 80, 80, 0.4);
    transform-origin: center;
    transition: all 0.4s ease-in-out;
    overflow: hidden;
    color: azure;
    width: 100%;
}

article a::after {
    position: absolute;
    inset-block: 0;
    inset-inline: 0;
    cursor: pointer;
    content: "";
}

article h2 {
    margin: 0 0 18px 0;
    font-size: 1.6rem;
    color: var(--title-color);
    transition: color 0.3s ease-out;
    background: var(--title-color);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

figure {
    margin: 0;
    padding: 0;
    aspect-ratio: 16 / 9;
    overflow: hidden;
    width: 100%;
}

article img {
    max-width: 100%;
    width: 100%;
    height: 100%;
    object-fit: cover;
    transform-origin: center;
    transform: scale(var(--img-scale));
    transition: transform 0.4s ease-in-out;
}

.article-body {
    padding: 24px;
}

article a {
    display: inline-flex;
    align-items: center;
    text-decoration: none;
    color: #28666e;
    cursor: pointer;
}

article a:focus {
    outline: 1px dotted #28666e;
}

article a .icon {
    min-width: 24px;
    width: 24px;
    height: 24px;
    margin-left: 5px;
    transform: translateX(var(--link-icon-translate));
    opacity: var(--link-icon-opacity);
    transition: all 0.3s;
}

article:has(:hover, :focus) {
    --img-scale: 1.1;
    --title-color: rgb(216, 180, 254);
    --link-icon-translate: 0;
    --link-icon-opacity: 1;
    cursor: pointer;
    transform: translateY(-10px);
    background: rgba(138, 43, 226, 0.5);
    /* border: 1px solid rgb(138, 43, 226, 1); */
}

.cards-container {
    display: grid;
    max-width: 1200px;
    min-height: 450px;
    margin-inline: auto;
    padding-inline: 24px;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
    width: 100%;
}

.go{
    color: #19f6e8;
    cursor: pointer;
}

@media screen and (max-width: 768px) {
    .cards-container {
        padding-inline: 16px;
        gap: 16px;
    }

    article h2 {
        font-size: 1.2rem;
    }

    .article-body {
        padding: 16px;
    }
}

@media screen and (max-width: 480px) {
    .cards-container {
        padding-inline: 12px;
        grid-template-columns: 1fr;
    }

    article {
        max-width: 100%;
    }

    article h2 {
        font-size: 1.1rem;
    }

    .article-body {
        padding: 12px;
    }
}
</style>
