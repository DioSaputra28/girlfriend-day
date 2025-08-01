<template>
  <section class="section-container relative" ref="heroSection">
    <div class="absolute inset-0 bg-gradient-to-br from-pink-100/50 via-rose-50/30 to-pink-200/40"></div>
    <div class="relative z-10 text-center max-w-md mx-auto">
      <!-- Floating Hearts Animation -->
      <div class="absolute -top-20 left-0 right-0 flex justify-center space-x-8 opacity-30">
        <div class="heart animate-bounce-gentle delay-0">💕</div>
        <div class="heart animate-bounce-gentle delay-150">💖</div>
        <div class="heart animate-bounce-gentle delay-300">💝</div>
      </div>
      
      <!-- Main Greeting -->
      <div class="space-y-6 animate-fade-in">
        <h1 class="text-4xl sm:text-5xl font-cursive font-semibold text-gradient mb-4">
          Halooo sayang
        </h1>
        
        <div class="bg-white/70 backdrop-blur-sm rounded-3xl p-8 shadow-lg border border-pink-200/50">
          <p class="text-lg sm:text-xl text-gray-700 font-medium leading-relaxed">
            Aku denger dengar hari ini itu Girlfriend Day ya? Jadi disini akuu mau ngucapin...
          </p>
        </div>
        
        <!-- Scroll Indicator -->
        <div class="mt-12 animate-pulse-gentle">
          <div class="flex flex-col items-center text-pink-600">
            <span class="text-sm font-medium mb-2">Scroll untuk melanjutkan</span>
            <div class="w-6 h-10 border-2 border-pink-400 rounded-full flex justify-center">
              <div class="w-1 h-3 bg-pink-400 rounded-full mt-2 animate-bounce"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const heroSection = ref<HTMLElement>()

onMounted(() => {
  // Add entrance animation delay
  if (heroSection.value) {
    heroSection.value.style.opacity = '0'
    setTimeout(() => {
      if (heroSection.value) {
        heroSection.value.style.opacity = '1'
        heroSection.value.style.transition = 'opacity 1s ease-in-out'
      }
    }, 300)
  }
})
</script>

<style scoped>
.heart {
  font-size: 2rem;
  animation-duration: 2s;
  animation-iteration-count: infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(5deg); }
}

.delay-0 { animation-delay: 0s; }
.delay-150 { animation-delay: 0.15s; }
.delay-300 { animation-delay: 0.3s; }
</style>