<template>
    <canvas ref="canvas" class="webgl"></canvas>
  </template>
  
  <script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  import * as THREE from 'three';
  import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';
  
  const canvas = ref(null);
  const count = 3000;
  const positions = new Float32Array(count * 3);
  const colors = new Float32Array(count * 3);
  const velocities = new Float32Array(count * 3);
  const mouse = new THREE.Vector2(0, 0);
  let scene, camera, renderer, particles, controls;
  let particlesGeometry;
  const sizes = {
    width: typeof window !== 'undefined' ? window.innerWidth : 800,
    height: typeof window !== 'undefined' ? window.innerHeight : 600,
  };
  const clock = new THREE.Clock();
  
  onMounted(() => {
    if (canvas.value) {
      init();
    } else {
      console.error('Canvas not found!');
    }
  });
  
  onBeforeUnmount(() => {
    cleanup();
  });
  
  function init() {
    scene = new THREE.Scene();
  
    // Initialisation des particules
    for (let i = 0; i < count; i++) {
      const i3 = i * 3;
      positions[i3] = (Math.random() - 0.5) * 10;
      positions[i3 + 1] = (Math.random() - 0.5) * 10;
      positions[i3 + 2] = (Math.random() - 0.5) * 10;
  
      const isPurple = Math.random() > 0.5;
      colors[i3] = isPurple ? 0.5 : 0;
      colors[i3 + 1] = isPurple ? 0 : 0;
      colors[i3 + 2] = isPurple ? 0.5 : 1;
  
      velocities[i3] = (Math.random() - 0.01) * 0.01;
      velocities[i3 + 1] = (Math.random() - 0.01) * 0.01;
      velocities[i3 + 2] = (Math.random() - 0.01) * 0.01;
    }
  
    particlesGeometry = new THREE.BufferGeometry();
    particlesGeometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    particlesGeometry.setAttribute('color', new THREE.BufferAttribute(colors, 3));
  
    const particlesMaterial = new THREE.PointsMaterial({
      size: 0.02,
      sizeAttenuation: true,
      vertexColors: true,
      transparent: true,
      depthWrite: false,
      blending: THREE.AdditiveBlending,
    });
  
    particles = new THREE.Points(particlesGeometry, particlesMaterial);
    scene.add(particles);
  
    camera = new THREE.PerspectiveCamera(50, sizes.width / sizes.height);
    camera.position.z = 8;
    scene.add(camera);
  
    controls = new OrbitControls(camera, canvas.value);
    controls.enableDamping = true;
  
    renderer = new THREE.WebGLRenderer({ canvas: canvas.value });
    renderer.setSize(sizes.width, sizes.height);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  
    if (typeof window !== 'undefined') {
      window.addEventListener('mousemove', onMouseMove);
      window.addEventListener('resize', onResize);
    }
  
    tick();
  }
  
  function onMouseMove(event) {
    if (typeof window !== 'undefined') {
      mouse.x = (event.clientX / sizes.width) * 2 - 1;
      mouse.y = -(event.clientY / sizes.height) * 2 + 1;
    }
  }
  
  function onResize() {
    if (typeof window !== 'undefined') {
      sizes.width = window.innerWidth;
      sizes.height = window.innerHeight;
  
      camera.aspect = sizes.width / sizes.height;
      camera.updateProjectionMatrix();
  
      renderer.setSize(sizes.width, sizes.height);
      renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    }
  }
  
  function tick() {
    const elapsedTime = clock.getElapsedTime();
  
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
  
      if (
        Math.abs(particlesGeometry.attributes.position.array[i3]) > 10 ||
        Math.abs(particlesGeometry.attributes.position.array[i3 + 1]) > 10 ||
        Math.abs(particlesGeometry.attributes.position.array[i3 + 2]) > 10
      ) {
        particlesGeometry.attributes.position.array[i3] = (Math.random() - 0.5) * 10;
        particlesGeometry.attributes.position.array[i3 + 1] = (Math.random() - 0.5) * 10;
        particlesGeometry.attributes.position.array[i3 + 2] = (Math.random() - 0.5) * 10;
      }
    }
  
    particlesGeometry.attributes.position.needsUpdate = true;
    controls.update();
    renderer.render(scene, camera);
    window.requestAnimationFrame(tick);
  }
  
  function cleanup() {
    if (typeof window !== 'undefined') {
      window.removeEventListener('mousemove', onMouseMove);
      window.removeEventListener('resize', onResize);
    }
  }
  </script>
  
  <style scoped>
  .webgl {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
  }
  </style>
  