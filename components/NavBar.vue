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
                        <a href="" class="nav-link block py-2 px-3 rounded md:p-0 text-white"
                            aria-current="page">Home</a>
                    </li>
                    <li>
                        <a href="#presentation" class="nav-link nav-link-text block py-2 px-3 text-white md:p-0">Présentation</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded md:p-0">Expérience</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded md:p-0">Passions</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white md:p-0">Contact</a>
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
</script>

<style scoped>
nav {
    position: fixed;
    overflow: hidden;
    z-index: 1;
    width: 100%;
}

.style {
    background-image: linear-gradient(0deg, rgb(9, 14, 2), rgba(138, 43, 226, 0.8));
    border: solid 1px rgb(123, 130, 193);
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
