<template>
    <div class="rounded-md mt-10 px-4 sm:px-0">
        <div class="flex flex-col sm:flex-row">
            <div class="w-full sm:w-1/2 text-white mb-6 sm:mb-0">
                <div class="name-container">
                    <h3 class="name text-center">
                        <span class="last-name">{{ identity.last_name }}</span>
                        <span class="first-name">{{ identity.first_name }}</span>
                    </h3>
                    <h3 class="contact text-center flex flex-col">{{ identity.job }}
                        <span class="ml-0 sm:ml-20"></span>
                    </h3>
                </div>
            </div>
            <div class="content text-white border rounded-md w-full sm:w-1/2 mx-4 sm:me-10 p-4">
                <h2 class="text-white font-bold text-center sm:text-left">CONTACT</h2>
                <div class="line h-px mx-4 sm:mx-10"></div>

                <div class="flex flex-col sm:flex-row">
                    <div class="lottie-container w-full sm:w-1/2">
                        <client-only>
                            <dotlottie-player
                                src="https://lottie.host/9bba1f7a-a258-4013-bd59-00390621202b/jyI5xNK6ed.lottie"
                                background="transparent" speed="1" class="lottie-player" loop
                                autoplay></dotlottie-player>
                        </client-only>
                    </div>
                    <div class="w-full sm:w-1/2 flex justify-center sm:justify-start mt-4 sm:mt-0">
                        <a href="mailto:danny.darragon.konki@gmail.com" class="mail">{{ identity.email }}</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import TextPlugin from "gsap/TextPlugin";
import SplitType from "split-type";

const identity = ref({
    last_name: "Darragon-Konki",
    first_name: "Danny",
    job: "Développeur web fullstack",
    email: "danny.darragon.konki@gmail.com",
});

// Émettre les données vers le parent
const emit = defineEmits(['identity']);
onMounted(() => {
    emit('identity', identity.value);
    import('@dotlottie/player-component');
//     // Text animation
//     gsap.registerPlugin(TextPlugin);
//     gsap.defaults({ ease: "none" });
//     const title = gsap.timeline({ repeat: -1, repeatDelay: 1, yoyo: true });
//     title.to("h3 span", {
//         duration: 4,
//         text: "{ à votre service }",
//     });

//     // Animation
//     const typeSplit = new SplitType(".animate", {
//         types: "lines, words, chars",
//         tagName: "span",
//     });

//     gsap.from(".animate .char", {
//         y: "100%",
//         opacity: 0,
//         rotateZ: 10,
//         duration: 0.5,
//         ease: "power1.out",
//         stagger: 0.1,
//         // repeat: 1,
//         // repeatDelay : 1,
//         // yoyo:true,
//     });
});
</script>

<style scoped>
.lottie-container {
    display: flex;
    justify-content: center;
    align-items: center;
}

.lottie-player {
    width: 200px;
    height: 200px;

    @media (min-width: 640px) {
        width: 300px;
        height: 300px;
    }
}

.content {
    background:
        linear-gradient(100deg, rgba(9, 14, 2, 0.9), rgba(138, 43, 226, 0.6));
}

.line {
    background: white;
}

h2 {
    margin: 0 0 18px 0;
    font-size: 1.2rem;
    margin-top: 2rem;

    @media (min-width: 640px) {
        font-size: 1.6rem;
        margin-left: 2rem;
    }
}

h3 {

    font-size: 1.5rem;

    @media (min-width: 640px) {
        font-size: 2rem;
    }
}

.mail {
    border: solid 1px rgba(138, 43, 226, 0.9);
    padding: 10px 15px;
    border-radius: 25px;
    margin: auto;
    font-size: 0.9rem;

    @media (min-width: 640px) {
        font-size: 1rem;
        margin-left: -2rem;
    }
}

.mail:hover {
    color: #ffffff;
    background-color: rgba(138, 43, 226, 0.6);
    transition: all 1s ease-out;
    box-shadow:
        0 4px 15px rgba(175, 2, 214, 0.6),
        0 0 30px rgba(175, 2, 214, 0.6);
}

.name-container {
    padding: 1rem;
    text-align: center;
}

.name {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-bottom: 1rem;
}

.last-name {
    font-size: 2.5rem;

    background: linear-gradient(to right, #fff, rgba(138, 43, 226, 0.8));
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    text-transform: uppercase;
    letter-spacing: 2px;
}

.first-name {
    font-size: 2rem;
    color: rgba(138, 43, 226, 0.8);

    letter-spacing: 1px;
}

@media (min-width: 640px) {
    .last-name {
        font-size: 3rem;
    }
    
    .first-name {
        font-size: 2.5rem;
    }
}
</style>
