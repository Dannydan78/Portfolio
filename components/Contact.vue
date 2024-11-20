<template>
    <div class="rounded-md mt-10">
        <div class="flex flex-row">
            <div class="lottie-container w-1/2">
                <client-only>
                    <dotlottie-player src="https://lottie.host/9bba1f7a-a258-4013-bd59-00390621202b/jyI5xNK6ed.lottie"
                        background="transparent" speed="1" class="lottie-player" loop autoplay></dotlottie-player>
                </client-only>
            </div>
            <div class="content text-white border rounded-md w-1/2">
                <h2 class="ml-5 text-white font-bold">CONTACT</h2>
    <div class="line h-px ml-10 mr-10"></div>
    <div class="lottie-container w-1/2">
                <client-only>
                    <dotlottie-player src="https://lottie.host/9bba1f7a-a258-4013-bd59-00390621202b/jyI5xNK6ed.lottie"
                        background="transparent" speed="1" class="lottie-player" loop autoplay></dotlottie-player>
                </client-only>
            </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted } from 'vue';

// Importation conditionnelle
onMounted(() => {
    import('@dotlottie/player-component').then(() => {
        console.log('Lottie player loaded');
    });
});
</script>

<style scoped>
.lottie-container {
    display: flex;
    justify-content: center;
    align-items: center;
}

.lottie-player {
    width: 300px;
    height: 300px;
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
  margin-left: 2rem;
  font-size: 1.6rem;
  margin-top: 2rem;
}
</style>