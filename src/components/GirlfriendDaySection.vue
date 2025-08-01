<template>
  <section class="section-container relative overflow-hidden" ref="sectionRef">
    <div class="absolute inset-0">
      <div class="absolute top-10 left-10 w-32 h-32 bg-pink-300/20 rounded-full blur-3xl"></div>
      <div class="absolute bottom-20 right-10 w-40 h-40 bg-rose-300/20 rounded-full blur-3xl"></div>
    </div>
    
    <div class="relative z-10 text-center max-w-lg mx-auto space-y-8" :class="{ 'animate-slide-up': isVisible }">
      <!-- Main Title -->
      <div class="relative">
        <h2 class="text-5xl sm:text-6xl font-elegant font-bold text-gradient mb-6">
          Happy
        </h2>
        <h2 class="text-4xl sm:text-5xl font-cursive font-semibold text-pink-600 -mt-2">
          Girlfriend Day
        </h2>
        
        <!-- Decorative elements -->
        <div class="absolute -top-8 -left-4 text-pink-400 text-2xl animate-spin" style="animation-duration: 8s;">
          🌸
        </div>
        <div class="absolute -bottom-4 -right-4 text-rose-400 text-2xl animate-spin" style="animation-duration: 10s; animation-direction: reverse;">
          🌺
        </div>
      </div>
      
      <!-- Message Card -->
      <div class="bg-gradient-to-br from-white/80 to-pink-50/60 backdrop-blur-sm rounded-3xl p-8 shadow-xl border border-pink-200/30 card-hover">
        <div class="space-y-4">
          <p class="text-lg text-gray-700 font-medium leading-relaxed">
            Shofia Jasmine(Justmine).
          </p>
          <p class="text-base text-gray-600 leading-relaxed">
            Iya aku mau ngucapin Happy Girlfriend Day ke kamu. Coba tebak, Siapa wanita yang canti banget, lucu banget, imut banget, DAN yang paling penting ini wanita ku? <br>
            YA CUMA KAMU LAH, YOU ONE AND ONLY.
          </p>
          <div class="pt-4">
            <span class="inline-block bg-gradient-to-r from-pink-500 to-rose-500 text-white px-6 py-2 rounded-full text-sm font-semibold">
              I LOVE YOU SO MUCH
            </span>
          </div>
        </div>
      </div>
      
      <!-- Date Badge -->
      <div class="inline-flex items-center bg-pink-100 text-pink-800 px-4 py-2 rounded-full text-sm font-semibold">
        {{ currentDate }}
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'

const sectionRef = ref<HTMLElement>()
const isVisible = ref(false)

const currentDate = computed(() => {
  return new Date().toLocaleDateString('id-ID', {
    weekday: 'long',
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  })
})

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