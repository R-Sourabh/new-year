<template>
  <ion-page class="black-background">
    <ion-content :fullscreen="true" class="black-content">
      <div class="logo-section ion-padding">
        <img ref="logoRef" :src="logoSrc" alt="Hotwax Commerce Logo" class="logo" />
      </div>
      <ion-item>
        <h1>Wrapped</h1>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import logo from '../images/True.png';

const logoSrc = logo;
const logoRef = ref(null);

onMounted(() => {
  if (logoRef.value) {
    // Create a timeline for the animation
    const tl = gsap.timeline();

    tl.fromTo(logoRef.value, 
      { opacity: 0, scale: 0.5, rotation: 0, y: 50 },
      { 
        opacity: 1, 
        scale: 1, 
        rotation: 360,
        y: 0, 
        duration: 1.5, 
        ease: "power2.out" 
      }
    )
    .to(logoRef.value, {
      scale: 1.1,
      duration: 0.5,
      yoyo: true,
      repeat: 1,
      ease: "power1.inOut"
    })
    .to(logoRef.value, {
      rotation: 0,
      duration: 0.5,
      ease: "power1.inOut"
    });
  }
});
</script>

<style scoped>
.black-background {
  background-color: black;
}

ion-content {
  --background: black;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.logo-section {
  text-align: center;
}

.logo {
  max-width: 80%;
  padding-top: 100px;
  height: 120px;
  width: 400px;
}
</style>