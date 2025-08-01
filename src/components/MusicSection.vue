<template>
  <section class="section-container bg-gradient-to-br from-pink-50 to-rose-100 relative" ref="sectionRef">
    <div class="absolute inset-0 opacity-10">
      <div class="absolute top-1/4 left-1/4 w-4 h-4 bg-pink-500 rounded-full animate-pulse"></div>
      <div class="absolute top-3/4 right-1/4 w-6 h-6 bg-rose-500 rounded-full animate-pulse delay-1000"></div>
      <div class="absolute top-1/2 left-3/4 w-3 h-3 bg-pink-400 rounded-full animate-pulse delay-500"></div>
    </div>
    
    <div class="relative z-10 text-center max-w-md mx-auto space-y-8" :class="{ 'animate-fade-in': isVisible }">
      <!-- Musical Notes Animation -->
      <div class="relative mb-8">
        <div class="flex justify-center space-x-4 text-4xl">
          <span class="animate-bounce delay-0">🎵</span>
          <span class="animate-bounce delay-150">🎶</span>
          <span class="animate-bounce delay-300">🎵</span>
        </div>
      </div>
      
      <!-- Instruction Text -->
      <div class="bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg border border-pink-200/50">
        <h3 class="text-xl font-semibold text-gray-800 mb-3">
          Sebelum lanjut scroll...
        </h3>
        <p class="text-gray-600 text-sm leading-relaxed mb-4">
          Play musik ini dulu ya sayang
        </p>
        
        <!-- Song Info -->
        <div class="bg-gradient-to-r from-pink-50 to-rose-50 rounded-lg p-3 mb-4 border border-pink-100">
          <div class="text-center">
            <h4 class="font-semibold text-gray-800 text-sm mb-1">🎵 Now Playing</h4>
            <p class="text-pink-600 font-medium text-sm">Godspeed</p>
            <p class="text-gray-500 text-xs">by Frank Ocean</p>
          </div>
        </div>
        
        <!-- Music Player Button -->
        <button
          @click="toggleMusic"
          :class="[
            'music-button',
            'w-full py-4 px-6 rounded-xl font-semibold text-white transition-all duration-300 transform hover:scale-105 active:scale-95',
            isPlaying 
              ? 'bg-gradient-to-r from-green-500 to-emerald-500 shadow-green-200' 
              : 'bg-gradient-to-r from-pink-500 to-rose-500 shadow-pink-200'
          ]"
          class="shadow-lg hover:shadow-xl"
        >
          <div class="flex items-center justify-center space-x-3">
            <span class="text-2xl">{{ isPlaying ? '⏸️' : '▶️' }}</span>
            <span>{{ isPlaying ? 'Music Playing...' : 'Play Our Song' }}</span>
          </div>
        </button>
      </div>
      
      <!-- Music Status -->
      <div v-if="isPlaying" class="bg-gradient-to-r from-green-100 to-emerald-100 rounded-lg p-4 text-green-800">
        <div class="flex items-center justify-center space-x-2 mb-2">
          <div class="w-2 h-6 bg-green-500 rounded animate-pulse"></div>
          <div class="w-2 h-8 bg-green-600 rounded animate-pulse delay-150"></div>
          <div class="w-2 h-4 bg-green-500 rounded animate-pulse delay-300"></div>
          <div class="w-2 h-7 bg-green-600 rounded animate-pulse delay-450"></div>
        </div>
        <p class="text-sm font-medium">Perfect! Sekarang scroll ke bawah ya</p>
      </div>
      
      <!-- Audio Element -->
      <audio
        ref="audioPlayer"
        loop
        preload="metadata"
      >
        <source src="/src/assets/lagu1.mp3" type="audio/mpeg">
      </audio>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const emit = defineEmits<{
  playMusic: []
}>()

const sectionRef = ref<HTMLElement>()
const audioPlayer = ref<HTMLAudioElement>()
const isVisible = ref(false)
const isPlaying = ref(false)

const toggleMusic = async () => {
  if (!audioPlayer.value) return
  
  try {
    if (isPlaying.value) {
      // Pause musik
      audioPlayer.value.pause()
      isPlaying.value = false
    } else {
      // Play musik dari file lagu.mp3
      await audioPlayer.value.play()
      isPlaying.value = true
      emit('playMusic')
    }
  } catch (error) {
    console.error('Error playing audio:', error)
    // Fallback jika audio tidak bisa diputar (misalnya karena autoplay policy)
    alert('Tidak bisa memutar audio. Pastikan Anda mengizinkan autoplay atau klik tombol lagi.')
  }
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          isVisible.value = true
        }
      })
    },
    { threshold: 0.3 }
  )
  
  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }
})
</script>

<style scoped>
.delay-0 { animation-delay: 0s; }
.delay-150 { animation-delay: 0.15s; }
.delay-300 { animation-delay: 0.3s; }
.delay-450 { animation-delay: 0.45s; }
.delay-500 { animation-delay: 0.5s; }
.delay-1000 { animation-delay: 1s; }
</style>