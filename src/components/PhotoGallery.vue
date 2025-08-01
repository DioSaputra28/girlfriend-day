<template>
  <section class="py-16 px-4 bg-gradient-to-br from-rose-50 to-pink-100 relative overflow-hidden">
    <!-- Background Decorations -->
    <div class="absolute inset-0 opacity-5">
      <div class="absolute top-20 left-10 text-6xl transform rotate-12">🌸</div>
      <div class="absolute top-40 right-20 text-4xl transform -rotate-12">💐</div>
      <div class="absolute bottom-32 left-20 text-5xl transform rotate-45">🌺</div>
    </div>

    <div class="max-w-lg mx-auto relative z-10">
      <!-- Section Title -->
      <div class="text-center mb-12">
        <h3 class="text-3xl font-cursive font-semibold text-gradient mb-2">
          Memories with You
        </h3>
        <p class="text-gray-600 text-sm">
          Setiap momen bersamamu adalah kenangan terindah 💕
        </p>
      </div>

      <!-- Photo Cards -->
      <div class="space-y-12">
        <!-- Photo 1 - Left aligned -->
        <div class="flex items-start space-x-4 animate-slide-up" :class="{ 'opacity-100': visibleCards.includes(0) }"
          ref="card0">
          <div class="flex-shrink-0">
            <div
              class="w-20 h-20 rounded-2xl bg-gradient-to-br from-pink-200 to-rose-300 shadow-lg flex items-center justify-center overflow-hidden">
              <img
                src="https://images.pexels.com/photos/1181686/pexels-photo-1181686.jpeg?auto=compress&cs=tinysrgb&w=200&h=200&fit=crop"
                alt="Shofia" class="w-full h-full object-cover" />
            </div>
          </div>
          <div
            class="flex-1 bg-white/70 backdrop-blur-sm rounded-2xl p-4 shadow-lg border border-pink-200/50 card-hover">
            <div class="flex items-start justify-between mb-2">
              <h4 class="font-semibold text-gray-800 text-sm">Senyuman Terindah</h4>
              <span class="text-pink-500 text-xs">💖</span>
            </div>
            <p class="text-gray-600 text-xs leading-relaxed">
              Setiap kali kamu tersenyum, dunia jadi terasa lebih cerah dan indah. Senyumanmu adalah keajaiban kecil
              yang selalu bikin aku bahagia.
            </p>
          </div>
        </div>

        <!-- Connecting Line -->
        <div class="flex justify-center">
          <div class="w-0.5 h-8 bg-gradient-to-b from-pink-300 to-rose-300 rounded-full"></div>
        </div>

        <!-- Photo 2 - Right aligned -->
        <div class="flex items-start space-x-4 flex-row-reverse animate-slide-up"
          :class="{ 'opacity-100': visibleCards.includes(1) }" ref="card1">
          <div class="flex-shrink-0">
            <div
              class="w-20 h-20 rounded-2xl bg-gradient-to-br from-rose-200 to-pink-300 shadow-lg flex items-center justify-center overflow-hidden">
              <img
                src="https://images.pexels.com/photos/1181674/pexels-photo-1181674.jpeg?auto=compress&cs=tinysrgb&w=200&h=200&fit=crop"
                alt="Shofia" class="w-full h-full object-cover" />
            </div>
          </div>
          <div
            class="flex-1 bg-white/70 backdrop-blur-sm rounded-2xl p-4 shadow-lg border border-pink-200/50 card-hover text-right">
            <div class="flex items-start justify-between mb-2 flex-row-reverse">
              <h4 class="font-semibold text-gray-800 text-sm">Mata Berbinar</h4>
              <span class="text-rose-500 text-xs">✨</span>
            </div>
            <p class="text-gray-600 text-xs leading-relaxed">
              Matamu seperti bintang yang bersinar terang di malam hari. Setiap kali aku menatap matamu, aku melihat
              masa depan yang indah bersama.
            </p>
          </div>
        </div>

        <!-- Connecting Line -->
        <div class="flex justify-center">
          <div class="w-0.5 h-8 bg-gradient-to-b from-rose-300 to-pink-300 rounded-full"></div>
        </div>

        <!-- Photo 3 - Left aligned -->
        <div class="flex items-start space-x-4 animate-slide-up" :class="{ 'opacity-100': visibleCards.includes(2) }"
          ref="card2">
          <div class="flex-shrink-0">
            <div
              class="w-20 h-20 rounded-2xl bg-gradient-to-br from-pink-200 to-rose-300 shadow-lg flex items-center justify-center overflow-hidden">
              <img
                src="https://images.pexels.com/photos/1181690/pexels-photo-1181690.jpeg?auto=compress&cs=tinysrgb&w=200&h=200&fit=crop"
                alt="Shofia" class="w-full h-full object-cover" />
            </div>
          </div>
          <div
            class="flex-1 bg-white/70 backdrop-blur-sm rounded-2xl p-4 shadow-lg border border-pink-200/50 card-hover">
            <div class="flex items-start justify-between mb-2">
              <h4 class="font-semibold text-gray-800 text-sm">Tawa yang Merdu</h4>
              <span class="text-pink-500 text-xs">🎵</span>
            </div>
            <p class="text-gray-600 text-xs leading-relaxed">
              Suara tawamu adalah musik terindah yang pernah aku dengar. Setiap kali kamu tertawa, hatiku ikut bergetar
              bahagia.
            </p>
          </div>
        </div>

        <!-- Connecting Line -->
        <div class="flex justify-center">
          <div class="w-0.5 h-8 bg-gradient-to-b from-pink-300 to-rose-300 rounded-full"></div>
        </div>

        <!-- Photo 4 - Right aligned -->
        <div class="flex items-start space-x-4 flex-row-reverse animate-slide-up"
          :class="{ 'opacity-100': visibleCards.includes(3) }" ref="card3">
          <div class="flex-shrink-0">
            <div
              class="w-20 h-20 rounded-2xl bg-gradient-to-br from-rose-200 to-pink-300 shadow-lg flex items-center justify-center overflow-hidden">
              <img
                src="https://images.pexels.com/photos/1181695/pexels-photo-1181695.jpeg?auto=compress&cs=tinysrgb&w=200&h=200&fit=crop"
                alt="Shofia" class="w-full h-full object-cover" />
            </div>
          </div>
          <div
            class="flex-1 bg-white/70 backdrop-blur-sm rounded-2xl p-4 shadow-lg border border-pink-200/50 card-hover text-right">
            <div class="flex items-start justify-between mb-2 flex-row-reverse">
              <h4 class="font-semibold text-gray-800 text-sm">Hati yang Baik</h4>
              <span class="text-rose-500 text-xs">💝</span>
            </div>
            <p class="text-gray-600 text-xs leading-relaxed">
              Kamu memiliki hati yang paling baik dan lembut. Kebaikanmu selalu menginspirasi aku untuk menjadi pribadi
              yang lebih baik setiap harinya.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const visibleCards = ref<number[]>([])
const card0 = ref<HTMLElement>()
const card1 = ref<HTMLElement>()
const card2 = ref<HTMLElement>()
const card3 = ref<HTMLElement>()

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        const cardElement = entry.target as HTMLElement
        const cardIndex = parseInt(cardElement.getAttribute('data-card-index') || '0')

        if (entry.isIntersecting && !visibleCards.value.includes(cardIndex)) {
          visibleCards.value.push(cardIndex)
          // Animate card when it becomes visible
          setTimeout(() => {
            cardElement.style.opacity = '1'
            cardElement.style.transform = 'translateY(0)'
          }, cardIndex * 150)
        }
      })
    },
    { threshold: 0.2 }
  )

  const cards = [card0.value, card1.value, card2.value, card3.value]
  cards.forEach((card, index) => {
    if (card) {
      // Set data attribute for identification
      card.setAttribute('data-card-index', index.toString())

      // Initially hide cards
      card.style.opacity = '0'
      card.style.transform = 'translateY(30px)'
      card.style.transition = 'all 0.6s ease-out'

      observer.observe(card)
    }
  })
})
</script>