<template>
  <section
    class="min-h-screen flex items-center justify-center bg-gradient-to-br from-pink-50 via-rose-50 to-pink-100 relative overflow-hidden"
    ref="sectionRef">
    <!-- Background Elements -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute top-1/4 left-1/6 w-32 h-32 bg-pink-300 rounded-full blur-3xl"></div>
      <div class="absolute bottom-1/4 right-1/6 w-40 h-40 bg-rose-300 rounded-full blur-3xl"></div>
    </div>

    <div class="text-center space-y-8 z-10 relative max-w-sm mx-auto px-4">
      <!-- Final Message -->
      <div class="space-y-4 mb-12">
        <h3 class="text-2xl sm:text-3xl font-cursive font-semibold text-gradient">
          Forever & Always
        </h3>
        <div class="bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg border border-pink-200/50">
          <p class="text-gray-700 text-sm leading-relaxed mb-4">
            Seperti bunga ini yang mekar dengan indah, cinta kita akan terus tumbuh dan berkembang seiring waktu.
          </p>
          <p class="text-pink-600 font-semibold text-sm">
            Happy Girlfriend Day, Shofia Jasmine! 💕
          </p>
        </div>
      </div>

      <!-- Blooming Flower Animation -->
      <div class="relative flex items-center justify-center" style="height: 400px;">
        <!-- BATANG BUNGA -->
        <div
          class="absolute left-1/2 transform -translate-x-1/2 bg-gradient-to-t from-green-600 to-green-500 rounded-full transition-all duration-1500 ease-out"
          :style="{
            width: '6px', /* Lebar batang - bisa diubah untuk batang lebih tebal/tipis */
            height: `${Math.min(stemHeight, 150)}px`, /* Tinggi maksimal batang - ubah 150 untuk batang lebih tinggi/pendek */
            bottom: '0px', /* Posisi dari bawah container - ubah untuk naik/turun batang */
            opacity: stemHeight > 0 ? 1 : 0,
            boxShadow: '0 2px 4px rgba(0,0,0,0.1)'
          }"></div>

        <!-- DAUN KIRI -->
        <div
          class="absolute left-1/2 w-10 h-5 bg-gradient-to-br from-green-400 to-green-500 rounded-full transition-all duration-1500 ease-out origin-right"
          :style="{
            bottom: '80px', /* Jarak dari bawah - ubah untuk naik/turun daun kiri */
            transform: `translateX(-50%) translateX(-24px) rotate(-45deg) scale(${leafScale})`, /* translateX(-24px) = jarak ke kiri dari batang */
            opacity: leafOpacity,
            boxShadow: '0 2px 6px rgba(0,0,0,0.1)'
          }"></div>
        <!-- DAUN KANAN -->
        <div
          class="absolute left-1/2 w-10 h-5 bg-gradient-to-bl from-green-400 to-green-500 rounded-full transition-all duration-1500 ease-out origin-left"
          :style="{
            bottom: '112px', /* Jarak dari bawah - ubah untuk naik/turun daun kanan */
            transform: `translateX(-50%) translateX(24px) rotate(45deg) scale(${leafScale})`, /* translateX(24px) = jarak ke kanan dari batang */
            opacity: leafOpacity,
            boxShadow: '0 2px 6px rgba(0,0,0,0.1)'
          }"></div>

        <!-- MATA BUNGA (CENTER KUNING) -->
        <div
          class="absolute left-1/2 w-8 h-8 bg-gradient-to-br from-yellow-300 to-orange-400 rounded-full transition-all duration-1500 ease-out z-10"
          :style="{
            top: '193px', /* UBAH INI untuk naik/turun mata bunga - semakin kecil semakin naik */
            transform: `translateX(-50%) translateY(-50%) scale(${centerScale})`,
            opacity: centerOpacity,
            boxShadow: isFullyBloomed ? '0 0 20px rgba(251, 191, 36, 0.4)' : '0 2px 8px rgba(0,0,0,0.1)'
          }"></div>

        <!-- CONTAINER KELOPAK BUNGA -->
        <div class="absolute left-1/2" :style="{
          top: '155px', /* UBAH INI untuk naik/turun seluruh kelopak - harus sejajar dengan mata bunga */
          transform: 'translateX(-50%)'
        }">
          <!-- Petal 1 - Top -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-pink-400 to-pink-300 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '-20px',
              left: '-10px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[0]}deg)`
            }"></div>

          <!-- Petal 2 - Top Right -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-pink-500 to-pink-400 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '-14px',
              left: '7px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[1]}deg)`
            }"></div>

          <!-- Petal 3 - Right -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-rose-400 to-pink-300 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '-2px',
              left: '14px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[2]}deg)`
            }"></div>

          <!-- Petal 4 - Bottom Right -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-pink-400 to-rose-300 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '10px',
              left: '7px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[3]}deg)`
            }"></div>

          <!-- Petal 5 - Bottom -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-rose-500 to-pink-400 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '16px',
              left: '-10px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[4]}deg)`
            }"></div>

          <!-- Petal 6 - Bottom Left -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-pink-500 to-rose-400 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '10px',
              left: '-27px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[5]}deg)`
            }"></div>

          <!-- Petal 7 - Left -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-pink-400 to-pink-300 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '-2px',
              left: '-34px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[6]}deg)`
            }"></div>

          <!-- Petal 8 - Top Left -->
          <div
            class="absolute w-5 h-10 bg-gradient-to-t from-rose-400 to-pink-400 rounded-full origin-bottom transition-all duration-1000 ease-out"
            :style="{
              top: '-14px',
              left: '-27px',
              opacity: petalOpacity,
              transform: `scale(${petalScale}) rotate(${petalRotations[7]}deg)`
            }"></div>
        </div>

        <!-- Sparkle Effects -->
        <div v-if="isFullyBloomed" class="absolute inset-0 pointer-events-none">
          <div v-for="sparkle in sparkles" :key="sparkle.id" class="absolute text-yellow-300 animate-ping" :style="{
            left: sparkle.x + '%',
            top: sparkle.y + '%',
            fontSize: sparkle.size + 'px',
            animationDelay: sparkle.delay + 's'
          }">
            ✨
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const sectionRef = ref<HTMLElement>()
const stemHeight = ref(0)
const leafOpacity = ref(0)
const leafScale = ref(0)
const centerOpacity = ref(0)
const centerScale = ref(0)
const petalOpacity = ref(0)
const petalScale = ref(0)
const petalRotations = ref([0, 45, 90, 135, 180, 225, 270, 315])
const isFullyBloomed = ref(false)

interface Sparkle {
  id: number
  x: number
  y: number
  size: number
  delay: number
}

const sparkles = ref<Sparkle[]>([])

const createSparkles = () => {
  sparkles.value = Array.from({ length: 8 }, (_, i) => ({
    id: i,
    x: Math.random() * 100,
    y: Math.random() * 100,
    size: Math.random() * 8 + 12,
    delay: Math.random() * 2
  }))
}

const updateFlowerAnimation = () => {
  if (!sectionRef.value) return

  const rect = sectionRef.value.getBoundingClientRect()
  const windowHeight = window.innerHeight
  const sectionTop = rect.top
  const sectionHeight = rect.height

  // Calculate scroll progress within the section - more sensitive trigger
  const scrollProgress = Math.max(0, Math.min(1, (windowHeight - sectionTop) / (windowHeight * 0.5)))

  // Start animation earlier when section comes into view
  if (scrollProgress > 0.1) {
    // Stem grows first
    stemHeight.value = Math.min(150, (scrollProgress - 0.1) * 167) // 150 / 0.9
  }

  if (scrollProgress > 0.2) {
    // Leaves appear and spread
    leafOpacity.value = Math.min(1, (scrollProgress - 0.2) * 1.25) // 1 / 0.8
    leafScale.value = Math.min(1, (scrollProgress - 0.2) * 1.25)
  }

  if (scrollProgress > 0.3) {
    // Flower center appears
    centerOpacity.value = Math.min(1, (scrollProgress - 0.3) * 1.43) // 1 / 0.7
    centerScale.value = Math.min(1.2, (scrollProgress - 0.3) * 1.71) // 1.2 / 0.7
  }

  if (scrollProgress > 0.4) {
    // Petals bloom with rotation
    petalOpacity.value = Math.min(1, (scrollProgress - 0.4) * 1.67) // 1 / 0.6
    petalScale.value = Math.min(1.1, (scrollProgress - 0.4) * 1.83) // 1.1 / 0.6

    // Animate petal rotations for realistic blooming effect
    const rotationProgress = Math.min(1, (scrollProgress - 0.4) * 1.67)
    const bloomAngle = rotationProgress * 30 // Petals spread outward
    petalRotations.value = [
      30 - bloomAngle,         // Top
      60 - bloomAngle * 0.8,  // Top Right
      110 - bloomAngle * 0.6,  // Right
      120 + bloomAngle * 0.6, // Bottom Right
      150 + bloomAngle,       // Bottom
      225 + bloomAngle * 0, // Bottom Left
      290 - bloomAngle * 0.6, // Left
      349 - bloomAngle * 0.8  // Top Left
    ]
  }

  if (scrollProgress > 0.7 && !isFullyBloomed.value) {
    isFullyBloomed.value = true
    createSparkles()
  }
}

onMounted(() => {
  window.addEventListener('scroll', updateFlowerAnimation)
  updateFlowerAnimation() // Initial call
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateFlowerAnimation)
})
</script>