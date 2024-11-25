<template>
  <div class="main mt-10 rounded-md" id="experience">
    <div class="flex flex-col lg:flex-row gap-4">
      <div class="card flex flex-col w-full lg:w-1/2 border border-gray-500 rounded-md">
        <h2 class="ml-5 text-white font-bold">EXPERIENCE</h2>
        <div class="line h-px ml-10 mr-10"></div>
        <div class="ml-8 text-gray-400 mt-4 m-2">Formation : Licence professionnelle de Concepteur développeur d'application (Bac +3)
        </div>
        <div class="m-4 text-white mt-8 rounded-md scroll-container">
          <div class="scroll-content flex flex-col">
            <div class="experience-item mb-6">
              <div class="flex flex-row ps-3 items-center gap-2">
                <p class="company-name font-bold text-purple-300">Free :</p>
                <p class="job-period bg-purple-900/30 px-2 py-1 rounded-md">STAGE (08/2023 - 11/2023)</p>
                <p class=""> - 3 mois </p>
              </div>
              <div class="job-title ps-3 text-lg font-medium mt-1">
                Développeur fullstack Laravel/Vue.js
              </div>
              <div class="job-description ps-3 text-gray-400 mt-2">
                <p>- Réalisations de projets avec Laravel / Vue.JS 3.<br>
                  - Consolidation du framework Laravel et de Vue.js.<br>
                  - Créations de composants customisé : Service / Route / Model / Controller.<br>
                  - Création d'une base de données SQL avec un MCD.<br>
                  - Exploration de Docker
                </p>
              </div>
            </div>

            <div class="experience-item mb-6">
              <div class="flex flex-row ps-3 items-center gap-2">
                <p class="company-name font-bold text-purple-300">Free :</p>
                <p class="job-period bg-purple-900/30 px-2 py-1 rounded-md">CDD (11/2023 - 12/2024)</p>
                <p class=""> - 13 mois </p>
              </div>
              <div class="job-title ps-3 text-lg font-medium mt-1">
                Développeur fullstack Laravel/Vue.js
              </div>
              <div class="job-description ps-3 text-gray-400 mt-2">
                <p>
                  - Développement de projets, front et back.<br>
                  - Langages : JavaScript, PHP, Laravel, Vue.js 3, Livewire 3<br>
                  - Projets cartographiques avec Leaflet.js et Vue.js 3 et utilisation de GeoServer<br>
                  - Gestion de base de données MySQL<br>
                  - Utilisation de Tailwind CSS pour styliser les interfaces<br>
                  - Tests unitaires avec PHPUnit<br>
                  - Rédaction de scripts PHP<br>
                  - Migrations de bases de données<br>
                  - Docker pour encapsuler l'application et ses dépendances dans des conteneurs isolés, pour facilité le
                  déploiement de l'application sur différents environnements<br>
                  - GitLab pour la gestion du code source, réalisation de tickets de travail et la collaboration avec
                  l'équipe<br>
                  - Projet en mode Agile sur GitLab, avec gestion des tâches en sprints et kanban
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- Deuxième card -->
      <div class="card2 border border-gray-500 w-full lg:w-1/2 rounded-md">
        <Charts />
      </div>
    </div>
    <h2 class="mt-2 text-center font-mono">
      <span class="text-blue-500">commit</span>
      <span class="text-gray-400">[main]</span><br />
      <span class="text-purple-400">message:</span>
      <span class="text-gray-300">"Ma curiosité et ma soif d'apprendre sont les moteurs de mon évolution
        professionnelle"</span>
    </h2>
    <div class="mt-2 text-center font-mono">
      <h2 class="text-gray-400">
        <span class="text-purple-500">while</span> (dev.hasPassion()) {<br />
        &nbsp;&nbsp;&nbsp;&nbsp;curiosité.explore();<br />
        &nbsp;&nbsp;&nbsp;&nbsp;connaissances.expand();<br />
        &nbsp;&nbsp;&nbsp;&nbsp;<span class="text-green-400">progression++;</span><br />
        }
      </h2>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, nextTick } from 'vue';


const startAutoScroll = () => {
  const container = document.querySelector('.scroll-container');
  const content = document.querySelector('.scroll-content');

  if (!container || !content) return;

  let scrollInterval;
  let isPaused = false;
  let scrollDirection = 1;

  const handleMouseEnter = () => {
    isPaused = true;
    container.style.overflowY = 'auto';
  };

  const handleMouseLeave = () => {
    isPaused = false;
    container.style.overflowY = 'hidden';
  };

  const scroll = () => {
    if (!isPaused) {
      container.scrollTop += scrollDirection;


      if (container.scrollTop + container.clientHeight >= content.scrollHeight) {
        scrollDirection = -1;
      } else if (container.scrollTop <= 0) {
        scrollDirection = 1;
      }
    }
  };

  container.addEventListener('mouseenter', handleMouseEnter);
  container.addEventListener('mouseleave', handleMouseLeave);

  scrollInterval = setInterval(scroll, 40);

  // Nettoyage
  onBeforeUnmount(() => {
    if (scrollInterval) {
      clearInterval(scrollInterval);
    }
    container.removeEventListener('mouseenter', handleMouseEnter);
    container.removeEventListener('mouseleave', handleMouseLeave);
  });
};

onMounted(() => {
  startAutoScroll();
});


</script>

<style scoped>
.scroll-container {
  max-height: 350px;
  overflow-y: hidden;
  position: relative;
  mask-image: linear-gradient(to bottom,
      transparent 0%,
      black 20%,
      black 80%,
      transparent 100%);
  -webkit-mask-image: linear-gradient(to bottom,
      transparent 0%,
      black 20%,
      black 80%,
      transparent 100%);
}

.scroll-content {
  padding: 20px 10px;
  transition: transform 0.3s ease-in-out;
}

.main {
  margin-left: 15rem;
  margin-right: 15rem;
  color: white;
}

h2 {
  margin: 0 0 18px 0;
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
}

.card {

  background:
    linear-gradient(100deg, rgba(9, 14, 2, 0.9), rgba(138, 43, 226, 0.6));

  min-height: 600px;
}

.card2 {
  background-image: linear-gradient(300deg, rgb(9, 14, 2), rgba(138, 43, 226, 0.6));
  /* url('/images/JavaScript-logo.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat; */
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 600px;
  padding: 1rem;
}

.line {
  background: white;
}

/* Animation pour le défilement */
@keyframes autoScroll {
  from {
    transform: translateY(0);
  }

  to {
    transform: translateY(-100%);
  }
}

.experience-item {
  border-left: 2px solid rgba(138, 43, 226, 0.6);
  padding-left: 1rem;
  position: relative;
}

.experience-item::before {
  content: '';
  position: absolute;
  left: -5px;
  top: 0;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: rgb(138, 43, 226);
}

.job-period {
  font-size: 0.9rem;
  border: 1px solid rgba(138, 43, 226, 0.3);
}

.job-title {
  color: #fff;
  font-weight: 500;
}

/* Ajout des media queries */
@media screen and (max-width: 1280px) {
  .main {
    margin-left: 8rem;
    margin-right: 8rem;
  }
}

@media screen and (max-width: 1024px) {
  .main {
    margin-left: 4rem;
    margin-right: 4rem;
  }
}

@media screen and (max-width: 768px) {
  .main {
    margin-left: 2rem;
    margin-right: 2rem;
  }

  .scroll-container {
    max-height: 180px;
  }
}

@media screen and (max-width: 480px) {
  .main {
    margin-left: 1rem;
    margin-right: 1rem;
  }

  .scroll-container {
    max-height: 160px;
  }

  h2 {
    font-size: 1.4rem;
  }
}
</style>