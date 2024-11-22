<template>
    <div class="contact-section" id="contact">

        <div class="header-container">
            <h2 class="name">
                <span class="last-name">{{ identity.last_name }}</span>
                <span class="first-name">{{ identity.first_name }}</span>
            </h2>
          
        </div>

        
        <div class="contact-container border border-gray-400">
            <h2 class="section-title">CONTACTEZ-MOI</h2>
            <div class="title-underline"></div>

            <div class="contact-content">
                <!-- Animation Lottie -->
                <div class="lottie-section">
                    <client-only>
                        <dotlottie-player
                            src="https://lottie.host/9bba1f7a-a258-4013-bd59-00390621202b/jyI5xNK6ed.lottie"
                            background="transparent" 
                            speed="1" 
                            class="lottie-player" 
                            loop
                            autoplay>
                        </dotlottie-player>
                    </client-only>
                </div>

        
                <div class="vertical-divider"></div>

               
                <div class="contact-links">
                    <a :href="`mailto:${identity.email}`" class="contact-link">
                        <i class="fas fa-envelope"></i>
                        <span>{{ identity.email }}</span>
                    </a>

                    <a :href="identity.github" target="_blank" class="contact-link">
                        <i class="fab fa-github"></i>
                        <span>Dannydan78</span>
                    </a>

                    <a :href="identity.linkedin" target="_blank" class="contact-link">
                        <i class="fab fa-linkedin"></i>
                        <span>LinkedIn</span>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
defineProps({
    identity: {
        type: Object,
        required: true
    }
});

onMounted(() => {
    import('@dotlottie/player-component');
});
</script>

<style scoped>
.contact-section {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 4rem 1rem;
}

.header-container {
    text-align: center;
    margin-bottom: 3rem;
}

.name {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    justify-content: center;
    align-items: center;
    margin-bottom: 1rem;
}

.last-name {
    font-size: 3rem;
    background: linear-gradient(to right, #fff, rgba(138, 43, 226, 0.8));
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    text-transform: uppercase;
    letter-spacing: 2px;
}

.first-name {
    font-size: 2.5rem;
    /* color: rgba(138, 43, 226, 0.8); */
    color:#fff;
    letter-spacing: 1px;
}

.job-title {
    font-size: 1.5rem;
    color: #fff;
    opacity: 0.9;
}

.contact-container {
    background: linear-gradient(100deg, rgba(9, 14, 2, 0.9), rgba(138, 43, 226, 0.6));
    border-radius: 15px;
    padding: 2rem;
    box-shadow: 0 8px 32px rgba(138, 43, 226, 0.2);
    
}

.section-title {
    color: white;
    font-size: 1.8rem;
    font-weight: bold;
    text-align: center;
    margin-bottom: 1rem;
}

.title-underline {
    height: 2px;
    background: linear-gradient(to right, transparent, white, transparent);
    margin: 1rem auto 2rem;
    width: 150px;
}

.contact-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 2rem;
    padding: 2rem;
    position: relative;
}

.lottie-section {
    flex: 1;
    max-width: 400px;
}

.lottie-player {
    width: 100%;
    height: 300px;
}

.contact-links {
    flex: 1;
    max-width: 400px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 2rem 0;
}

.contact-link {
    display: flex;
    align-items: center;
    gap: 2rem;
    padding: 1.2rem 1.8rem;
    border-radius: 50px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(138, 43, 226, 0.6);
    color: white;
    transition: all 0.3s ease;
    position: relative;

    i {
        font-size: 1.5rem;
        width: 30px;
        text-align: center;
        transition: all 0.3s ease;
    }

    span {
  
        letter-spacing: 0.5px;
    }

    &:hover {
        background: rgba(138, 43, 226, 0.2);
        transform: translateX(10px);
        box-shadow: 
            0 4px 15px rgba(138, 43, 226, 0.3),
            0 0 30px rgba(25, 246, 232, 0.2);

        i {
            transform: scale(1.2);
            color: #19f6e8;
        }
    }
}

.vertical-divider {
    width: 3px;
    height: 250px;
    background: linear-gradient(
        to bottom,
        transparent 0%,
        rgba(138, 43, 226, 1) 20%,
        #19f6e8 50%,
        rgba(138, 43, 226, 1) 80%,
        transparent 100%
    );
    position: relative;
    margin: 0 2rem;
    box-shadow: 0 0 15px rgba(138, 43, 226, 0.6);
    animation: glowingDivider 3s ease-in-out infinite;
}

.vertical-divider::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 10px;
    height: 10px;
    background: #19f6e8;
    border-radius: 50%;
    box-shadow: 0 0 15px #19f6e8;
}

@keyframes glowingDivider {
    0%, 100% {
        opacity: 0.7;
        box-shadow: 0 0 10px rgba(138, 43, 226, 0.4);
    }
    50% {
        opacity: 1;
        box-shadow: 0 0 20px rgba(138, 43, 226, 0.8),
                    0 0 30px rgba(25, 246, 232, 0.4);
    }
}

/* Animation d'entrée pour chaque lien */
.contact-link:nth-child(1) { animation: slideIn 0.5s ease forwards; }
.contact-link:nth-child(2) { animation: slideIn 0.5s ease forwards 0.2s; }
.contact-link:nth-child(3) { animation: slideIn 0.5s ease forwards 0.4s; }

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateX(-20px);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

/* Responsive design */
@media (max-width: 768px) {
    .contact-section {
        padding: 2rem 1rem;
    }

    .last-name {
        font-size: 2.5rem;
    }

    .first-name {
        font-size: 2rem;
    }

    .job-title {
        font-size: 1.2rem;
    }

    .contact-container {
        padding: 1.5rem;
    }

    .contact-content {
        flex-direction: column;
        padding: 1rem;
    }

    .vertical-divider {
        width: 80%;
        height: 3px;
        margin: 2rem 0;
        background: linear-gradient(
            to right,
            transparent 0%,
            rgba(138, 43, 226, 1) 20%,
            #19f6e8 50%,
            rgba(138, 43, 226, 1) 80%,
            transparent 100%
        );
    }

    .contact-links {
        gap: 2rem;
        padding: 1.5rem 0;
        width: 100%;
    }

    .contact-link {
        padding: 1rem 1.5rem;
    }

    .contact-link i {
        font-size: 1.3rem;
    }

    .contact-link span {
        font-size: 1rem;
    }

    .vertical-divider::before {
        animation: moveBallHorizontal 3s ease-in-out infinite;
    }

    @keyframes moveBallHorizontal {
        0%, 100% {
            left: 20%;
            transform: translateX(0);
        }
        50% {
            left: 80%;
            transform: translateX(0);
        }
    }
}
</style>
