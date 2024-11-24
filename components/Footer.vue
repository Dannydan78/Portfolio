<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="quick-links">
        <a @click.prevent="props.scrollToSection('accueil')" href="#">Accueil</a>
        <a @click.prevent="props.scrollToSection('presentation')" href="#">Présentation</a>
        <a @click.prevent="props.scrollToSection('experience')" href="#">Expérience</a>
        <a @click.prevent="props.scrollToSection('passions')" href="#">Passions</a>
        <a @click.prevent="props.scrollToSection('contact')" href="#">Contact</a>
      </div>

      <div class="social-links">
        <a :href="identity.github" target="_blank" class="social-link">
          <i class="fab fa-github"></i>
        </a>
        <a :href="`mailto:${identity.email}`" class="social-link">
          <i class="fas fa-envelope"></i>
        </a>
        <a :href="identity.linkedin" target="_blank" class="social-link">
          <i class="fab fa-linkedin"></i>
        </a>
      </div>

      <div class="copyright">
        <p>&copy; {{ new Date().getFullYear() }} {{ identity.first_name }} {{ identity.last_name }}. Tous droits réservés.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const props = defineProps({
    identity: {
        type: Object,
        required: true
    },
    scrollToSection: {
        type: Function,
        required: true
    }
});

const { identity } = props;
</script>
<style scoped>
.footer {
    background: rgba(79, 80, 80, 0.3);
  color: #fff;
  padding: 2rem 0;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  min-height: 100px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}



.social-link {
  color: #fff;
  font-size: 1.5rem;
  transition: all 0.3s ease;
  margin-right: 2rem;
}

.social-link:hover {

}

.copyright {
  text-align: center;
  font-size: 0.9rem;
  color: #a0a0a0;
}

.quick-links {
  display: flex;
  gap: 1.5rem;
}

.quick-links a {
  color: #fff;
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s ease;
  position: relative;
}

.quick-links a::after {

  position: absolute;
  width: 0;
  height: 2px;
  bottom: -4px;
  left: 0;
  background-color: rgba(138, 43, 226, 1);
  transition: width 0.3s ease;
}

.quick-links a:hover {
    color: rgba(138, 43, 226, 1);
    transition: all 0.5s ease-out;

}

.quick-links a:hover::after {
  width: 100%;
}

@media (min-width: 768px) {
  .footer-content {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  .social-links {
    order: 2;
  }

  .copyright {
    order: 1;
  }

  .quick-links {
    order: 3;
  }
}

@media (max-width: 767px) {
  .footer-content {
    flex-direction: column;
    gap: 2rem;
  }

  .quick-links {
    order: 2;
  }

  .social-links {
    order: 1;
  }

  .copyright {
    order: 3;
  }
}
</style>