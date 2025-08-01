<template>
  <div class="app">
    <!-- Hero Section -->
    <HeroSection />
    
    <!-- Girlfriend Day Section -->
    <GirlfriendDaySection />
    
    <!-- Music Player Section -->
    <MusicSection @play-music="handlePlayMusic" />
    
    <!-- Photo Gallery Section -->
    <PhotoGallery />
    
    <!-- Blooming Flower Section -->
    <BloomingFlower />
  </div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted } from 'vue'
import HeroSection from './components/HeroSection.vue'
import GirlfriendDaySection from './components/GirlfriendDaySection.vue'
import MusicSection from './components/MusicSection.vue'
import PhotoGallery from './components/PhotoGallery.vue'
import BloomingFlower from './components/BloomingFlower.vue'

const handlePlayMusic = () => {
  console.log('Music started playing')
}

onMounted(() => {
  // Add smooth scrolling behavior
  document.documentElement.style.scrollBehavior = 'smooth'
})

onUnmounted(() => {
  document.documentElement.style.scrollBehavior = 'auto'
})
</script>

<style scoped>
.app {
  width: 100%;
  overflow-x: hidden;
}
</style>