<template>
    <nav class="style navTest">
        <div class="max-w-screen-xl mx-auto flex flex-wrap items-center justify-center p-4 relative">
            <!-- Hamburger Button -->
            <button
                @click="toggleMenu"
                class="block md:hidden text-white focus:outline-none mr-auto"
                aria-label="Toggle navigation"
            >
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                </svg>
            </button>
            
            <!-- Navigation Links -->
            <div :class="['w-full md:w-auto', isMenuOpen ? 'block' : 'hidden', 'md:block']">
                <ul class="flex flex-col md:flex-row md:space-x-16 mt-4 md:mt-0">
                    <li class="home">
                        <a @click.prevent="scrollToSection('home')" href="#" 
                           class="nav-link block py-2 px-3 rounded md:p-0 text-white cursor-pointer"
                           aria-current="page">Home</a>
                    </li>
                    <li>
                        <a @click.prevent="scrollToSection('presentation')" href="#" 
                           class="nav-link nav-link-text block py-2 px-3 text-white md:p-0 cursor-pointer">Présentation</a>
                    </li>
                    <li>
                        <a @click.prevent="scrollToSection('experience')" href="#" 
                           class="nav-link block py-2 px-3 text-white rounded md:p-0 cursor-pointer">Expérience</a>
                    </li>
                    <li>
                        <a @click.prevent="scrollToSection('passions')" href="#" 
                           class="nav-link block py-2 px-3 text-white rounded md:p-0 cursor-pointer">Passions</a>
                    </li>
                    <li>
                        <a @click.prevent="scrollToSection('contact')" href="#" 
                           class="nav-link block py-2 px-3 text-white md:p-0 cursor-pointer">Contact</a>
                    </li>
                </ul>
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
</script>

<style scoped>
nav {
    position: fixed;
    overflow: hidden;
    z-index: 1;
    width: 100%;
}

.style {
    background-image: linear-gradient(0deg, rgb(9, 14, 2), rgba(138, 43, 226, 0.9));
    border-bottom: solid 0.5px rgb(123, 130, 193);
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
}

.nav-link {
    border: solid 1px rgba(138, 43, 226, 0.9);
    padding: 10px 15px;
    border-radius: 25px;
}

.nav-link:hover {
    color: #ffffff;
    background-color: rgba(138, 43, 226, 0.6);
    transition: all 1s ease-out;
    box-shadow:
        0 4px 15px rgba(175, 2, 214, 0.6),
        0 0 30px rgba(175, 2, 214, 0.6);
  
}
</style>
