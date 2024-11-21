<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="social-links">
        <a href="https://github.com/DannyDarragon" target="_blank" class="social-link">
          <i class="fab fa-github"></i>
        </a>
        <a :href="`mailto:${props.identity.email}`" class="social-link">
          <i class="fas fa-envelope"></i>
        </a>
        <a :href="`https://linkedin.com/in/${props.identity.linkedin}`" target="_blank" class="social-link">
          <i class="fab fa-linkedin"></i>
        </a>
      </div>

      <div class="copyright">
        <p>&copy; {{ new Date().getFullYear() }} {{ props.identity.first_name }} {{ props.identity.last_name }}. Tous droits réservés.</p>
      </div>

      <div class="quick-links">
        <a href="#home">Accueil</a>
        <a href="#about">Présentation</a>
        <a href="#experience">Expérience</a>
        <a href="#passions">Passions</a>
        <a href="#contact">Contact</a>
      </div>
    </div>
  </footer>
</template>

<script setup>
const props = defineProps({
    identity: {
      type: Object,
      required: true
    }
});
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
  color: rgba(138, 43, 226, 1);
  transform: translateY(-3px);
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
  content: '';
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
}

.quick-links a:hover::after {
  width: 100%;
}

/* Responsive Design */
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
  .quick-links {
    flex-wrap: wrap;
    justify-content: center;
    text-align: center;
  }
}
</style>