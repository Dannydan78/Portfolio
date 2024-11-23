<template>
    <nav class="style navTest">
        <div class="max-w-screen-xl w-full mx-auto flex items-center justify-between p-4 relative">
            <!-- Hamburger Button -->
            <button @click="toggleMenu" class="block lg:hidden text-white focus:outline-none"
                aria-label="Toggle navigation">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7">
                    </path>
                </svg>
            </button>

            <!-- Menu mobile -->
            <div
                :class="['w-full lg:flex lg:items-center lg:justify-between', isMenuOpen ? 'block' : 'hidden', 'lg:block']">
                <!-- Navigation Link -->
                <ul class="flex flex-col lg:flex-row lg:justify-center lg:space-x-16 mt-4 lg:mt-0 mx-auto">
                    <li class="mb-2 lg:mb-0">
                        <a @click.prevent="scrollToSection('accueil')" href="#"
                            class="nav-link block py-2 px-3 text-white cursor-pointer" aria-current="page">Accueil</a>
                    </li>
                    <li class="mb-2 lg:mb-0">
                        <a @click.prevent="scrollToSection('presentation')" href="#"
                            class="nav-link block py-2 px-3 text-white cursor-pointer">Présentation</a>
                    </li>
                    <li class="mb-2 lg:mb-0">
                        <a @click.prevent="scrollToSection('experience')" href="#"
                            class="nav-link block py-2 px-3 text-white cursor-pointer">Expérience</a>
                    </li>
                    <li class="mb-2 lg:mb-0">
                        <a @click.prevent="scrollToSection('passions')" href="#"
                            class="nav-link block py-2 px-3 text-white cursor-pointer">Passions</a>
                    </li>
                    <li class="mb-2 lg:mb-0">
                        <a @click.prevent="scrollToSection('contact')" href="#"
                            class="nav-link block py-2 px-3 text-white cursor-pointer">Contact</a>
                    </li>
                </ul>
                <div class="social-icons-container ml-auto hidden lg:block">
                    <div class="flex justify-end space-x-6 mt-6 lg:mt-0">
                        <a href="https://github.com/Dannydan78" target="_blank" class="social-link">
                            <i class="fab fa-github"></i>
                        </a>
                        <a href="https://www.linkedin.com" target="_blank" class="social-link">
                            <i class="fab fa-linkedin"></i>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);

function toggleMenu() {
    isMenuOpen.value = !isMenuOpen.value;
}

function scrollToSection(sectionId) {
    const element = document.getElementById(sectionId);
    if (element) {
        isMenuOpen.value = false;

        const navbarHeight = 80;
        const elementPosition = element.getBoundingClientRect().top;
        const offsetPosition = elementPosition + window.pageYOffset - navbarHeight;

        window.scrollTo({
            top: offsetPosition,
            behavior: 'smooth'
        });
    }
}
defineExpose({
    scrollToSection
});
</script>

<style scoped>
nav {
    position: fixed;
    overflow: hidden;
    z-index: 1000;
    width: 100%;
}

.style {
    background-image: linear-gradient(0deg, rgb(9, 14, 2), rgba(138, 43, 226, 0.9));
    border-bottom: solid 0.5px rgb(123, 130, 193);
    top: 0;
    left: 0;
    right: 0;
}

.nav-link {
    border: solid 1px rgba(138, 43, 226, 0.9);
    padding: 10px 15px;
    border-radius: 25px;
    transition: all 0.3s ease;
    display: block;
    text-align: center;
}

.nav-link:hover {
    color: #ffffff;
    background-color: rgba(138, 43, 226, 0.6);
    box-shadow:
        0 4px 15px rgba(175, 2, 214, 0.6),
        0 0 30px rgba(175, 2, 214, 0.6);
}

.social-link {
    color: white;
    font-size: 1.5rem;
    transition: all 0.3s ease;
    padding: 8px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.social-link:hover {}

.social-icons-container {
    @media (min-width: 768px) {
        margin-left: 2rem;
        min-width: 120px;
    }
}

/* Mobile styles */
@media (max-width: 768px) {
    .nav-link {
        margin: 0.5rem 1rem;
        padding: 0.8rem 1rem;
    }

    .social-link {
        font-size: 1.2rem;
    }

    [class*="isMenuOpen"] {
        background: rgba(9, 14, 2, 0.95);
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        padding: 1rem;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
        box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        display: flex;
        flex-direction: column;
    }

    .social-icons-container {
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid rgba(255, 255, 255, 0.1);
    }

    .social-link {
        font-size: 1.5rem;
        padding: 0.5rem;
    }

    /* Animation du menu mobile */
    .block {
        animation: slideDown 0.3s ease-out;
    }

    @keyframes slideDown {
        from {
            opacity: 0;
            transform: translateY(-10px);
        }

        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
}

/* Ajustements pour les grands écrans */
@media (min-width: 769px) {
    nav>div {
        padding: 1rem 2rem;
    }

    .nav-link {
        margin: 0;
        white-space: nowrap;
    }
}
</style>
