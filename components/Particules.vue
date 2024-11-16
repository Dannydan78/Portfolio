<template>
  <canvas ref="canvas" class="webgl"></canvas>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';

const canvas = ref(null);
const count = 10000;
const positions = new Float32Array(count * 3);
const colors = new Float32Array(count * 3);
const velocities = new Float32Array(count * 3);
const mouse = new THREE.Vector2(0, 0);
let scene, camera, renderer, particles, controls;
let particlesGeometry;
const clock = new THREE.Clock();
let sizes = { width: 0, height: 0 };

onMounted(() => {
  // Obtenir la hauteur totale du document
  const documentHeight = Math.max(
    document.body.scrollHeight,
    document.body.offsetHeight,
    document.documentElement.clientHeight,
    document.documentElement.scrollHeight,
    document.documentElement.offsetHeight
  );
  
  sizes.width = window.innerWidth;
  sizes.height = documentHeight; // Utiliser la hauteur totale du document
  init();

  // Observer les changements de taille du contenu
  const resizeObserver = new ResizeObserver((entries) => {
    const documentHeight = Math.max(
      document.body.scrollHeight,
      document.body.offsetHeight,
      document.documentElement.clientHeight,
      document.documentElement.scrollHeight,
      document.documentElement.offsetHeight
    );
    sizes.height = documentHeight;
    onResize();
  });

  resizeObserver.observe(document.body);
});

onBeforeUnmount(() => {
  cleanup();
});

function init() {
  if (!canvas.value) {
    console.error('Canvas not found!');
    return;
  }

  scene = new THREE.Scene();

  // Distribution des particules sur toute la hauteur
  const aspectRatio = sizes.width / sizes.height;
  const distributionHeight = 40 * (sizes.height / sizes.width); // Ajuster la distribution en fonction du ratio

  for (let i = 0; i < count; i++) {
    const i3 = i * 3;
    positions[i3] = (Math.random() - 0.5) * 40;
    positions[i3 + 1] = (Math.random() - 0.5) * distributionHeight; // Distribution verticale adaptée
    positions[i3 + 2] = (Math.random() - 0.5) * 40;

    // Colors
    const isPurple = Math.random() > 0.5;
    colors[i3] = isPurple ? 0.5 : 0;
    colors[i3 + 1] = isPurple ? 0 : 0;
    colors[i3 + 2] = isPurple ? 0.5 : 1;

    // Vitesses
    velocities[i3] = (Math.random() - 0.01) * 0.008;
    velocities[i3 + 1] = (Math.random() - 0.01) * 0.008;
    velocities[i3 + 2] = (Math.random() - 0.01) * 0.008;
  }

  particlesGeometry = new THREE.BufferGeometry();
  particlesGeometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  particlesGeometry.setAttribute('color', new THREE.BufferAttribute(colors, 3));

  const particlesMaterial = new THREE.PointsMaterial({
    size: 0.05,
    sizeAttenuation: true,
    vertexColors: true,
    transparent: true,
    depthWrite: false,
    blending: THREE.AdditiveBlending
  });

  particles = new THREE.Points(particlesGeometry, particlesMaterial);
  scene.add(particles);

  // Camera adaptée à la hauteur
  const fov = 45;
  camera = new THREE.PerspectiveCamera(fov, sizes.width / sizes.height, 0.1, 2000);
  camera.position.z = 50; // Reculé davantage pour voir toute la scène
  camera.lookAt(0, 0, 0);

  scene.add(camera);

  // Controls
  controls = new OrbitControls(camera, canvas.value);
  controls.enableDamping = true;
  controls.enabled = false; // Désactiver les contrôles pour un fond fixe

  // Renderer avec la hauteur totale
  renderer = new THREE.WebGLRenderer({ 
    canvas: canvas.value,
    alpha: false // Désactiver la transparence
  });
  renderer.setClearColor(0x000000); // Définir la couleur de fond en noir
  renderer.setSize(sizes.width, sizes.height);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

  window.addEventListener('mousemove', onMouseMove);
  window.addEventListener('resize', onResize);
  window.addEventListener('scroll', onScroll);

  // Animation
  tick();
}

function onMouseMove(event) {
  mouse.x = (event.clientX / sizes.width) * 2 - 1;
  mouse.y = - ((event.clientY + window.scrollY) / sizes.height) * 2 + 1;
}

function onScroll() {
  // Mettre à jour la position de la caméra en fonction du scroll
  const scrollPercent = window.scrollY / (sizes.height - window.innerHeight);
  camera.position.y = -(scrollPercent * 20); 
  camera.lookAt(0, camera.position.y, 0);
}

function onResize() {
  // Mettre à jour la taille du renderer
  sizes.width = window.innerWidth;
  
  camera.aspect = sizes.width / sizes.height;
  camera.updateProjectionMatrix();

  renderer.setSize(sizes.width, sizes.height);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
}

function tick() {
  const elapsedTime = clock.getElapsedTime();
  const aspectRatio = sizes.width / sizes.height;
  const distributionHeight = 40 * (sizes.height / sizes.width);

  for (let i = 0; i < count; i++) {
    const i3 = i * 3;

    particlesGeometry.attributes.position.array[i3] += velocities[i3];
    particlesGeometry.attributes.position.array[i3 + 1] += velocities[i3 + 1];
    particlesGeometry.attributes.position.array[i3 + 2] += velocities[i3 + 2];

    const particlePosition = new THREE.Vector3(
      particlesGeometry.attributes.position.array[i3],
      particlesGeometry.attributes.position.array[i3 + 1],
      particlesGeometry.attributes.position.array[i3 + 2]
    );

    const distance = particlePosition.distanceTo(camera.position);
    const force = 0.9;

    if (mouse.x > -1 && mouse.x < 1 && mouse.y > -1 && mouse.y < 1) {
      const direction = new THREE.Vector3();
      direction.subVectors(particlePosition, camera.position);
      direction.normalize();

      particlesGeometry.attributes.position.array[i3] += direction.x * force / distance;
      particlesGeometry.attributes.position.array[i3 + 1] += direction.y * force / distance;
      particlesGeometry.attributes.position.array[i3 + 2] += direction.z * force / distance;
    }

    // Réinitialiser les particules qui sortent des limites
    if (
      Math.abs(particlesGeometry.attributes.position.array[i3]) > 40 ||
      Math.abs(particlesGeometry.attributes.position.array[i3 + 1]) > distributionHeight ||
      Math.abs(particlesGeometry.attributes.position.array[i3 + 2]) > 40
    ) {
      particlesGeometry.attributes.position.array[i3] = (Math.random() - 0.5) * 40;
      particlesGeometry.attributes.position.array[i3 + 1] = (Math.random() - 0.5) * distributionHeight;
      particlesGeometry.attributes.position.array[i3 + 2] = (Math.random() - 0.5) * 40;
    }
  }

  particlesGeometry.attributes.position.needsUpdate = true;
  controls.update();
  renderer.render(scene, camera);
  window.requestAnimationFrame(tick);
}

function cleanup() {
  window.removeEventListener('mousemove', onMouseMove);
  window.removeEventListener('resize', onResize);
  window.removeEventListener('scroll', onScroll);
}
</script>

<style scoped>
.webgl {
  position: fixed; /* Fixed instead of absolute to couvrir tout l'écran */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: -1;
}

:global(body) {
  background-color: black;
}
</style>