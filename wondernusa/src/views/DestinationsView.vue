<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const natureDestinations = [
  {
    name: 'Taman Nasional Komodo',
    image: 'https://images.unsplash.com/photo-1596422846543-75c6fc197f07?auto=format&fit=crop&w=800&q=80',
    description: 'Habitat alami komodo dragon yang dilindungi UNESCO',
    location: 'Nusa Tenggara Timur'
  },
  {
    name: 'Raja Ampat',
    image: 'https://images.unsplash.com/photo-1559827260-dc66d52bef19?auto=format&fit=crop&w=800&q=80',
    description: 'Surga terumbu karang dengan biodiversitas laut terkaya',
    location: 'Papua Barat'
  },
  {
    name: 'Danau Toba',
    image: 'https://images.unsplash.com/photo-1505142468610-359e7d316be0?auto=format&fit=crop&w=800&q=80',
    description: 'Danau vulkanik terbesar di Asia Tenggara',
    location: 'Sumatera Utara'
  }
]

const beachDestinations = [
  {
    name: 'Pantai Kuta Bali',
    image: 'https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=800&q=80',
    description: 'Pantai ikonik dengan sunset spektakuler dan ombak sempurna',
    location: 'Bali'
  },
  {
    name: 'Gili Trawangan',
    image: 'https://images.unsplash.com/photo-1559827260-dc66d52bef19?auto=format&fit=crop&w=800&q=80',
    description: 'Pulau tropis dengan pasir putih dan air laut kristal',
    location: 'Lombok'
  },
  {
    name: 'Pink Beach',
    image: 'https://images.unsplash.com/photo-1505142468610-359e7d316be0?auto=format&fit=crop&w=800&q=80',
    description: 'Pantai dengan pasir pink yang langka dan memukau',
    location: 'Labuan Bajo'
  }
]

const highlandDestinations = [
  {
    name: 'Bromo Tengger Semeru',
    image: 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=800&q=80',
    description: 'Dataran tinggi vulkanik dengan sunrise menakjubkan',
    location: 'Jawa Timur'
  },
  {
    name: 'Dieng Plateau',
    image: 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=800&q=80',
    description: 'Dataran tinggi dengan candi kuno dan kawah belerang',
    location: 'Jawa Tengah'
  },
  {
    name: 'Gunung Rinjani',
    image: 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=800&q=80',
    description: 'Gunung tertinggi kedua dengan danau kawah Segara Anak',
    location: 'Lombok'
  }
]

// Carousel images
const carouselImages = [
  'https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=1600&q=80',
  'https://images.unsplash.com/photo-1555400038-63f5ba517a47?auto=format&fit=crop&w=1600&q=80',
  'https://images.unsplash.com/photo-1559827260-dc66d52bef19?auto=format&fit=crop&w=1600&q=80',
  'https://images.unsplash.com/photo-1518548419970-58e3b4079ab2?auto=format&fit=crop&w=1600&q=80'
]

const currentSlide = ref(0)
let carouselInterval = null

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % carouselImages.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + carouselImages.length) % carouselImages.length
}

const goToSlide = (index) => {
  currentSlide.value = index
}

onMounted(() => {
  carouselInterval = setInterval(() => {
    nextSlide()
  }, 5000)
})

onUnmounted(() => {
  if (carouselInterval) {
    clearInterval(carouselInterval)
  }
})
</script>

<template>
  <div class="font-sans text-slate-900 bg-slate-100 min-h-screen">
    <!-- CAROUSEL HERO -->
    <section class="relative w-full h-screen overflow-hidden">
      <div
        class="flex h-full transition-transform duration-800 ease-in-out"
        :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
      >
        <div
          v-for="(image, index) in carouselImages"
          :key="index"
          class="min-w-full h-full bg-cover bg-center brightness-75"
          :style="{ backgroundImage: `url(${image})` }"
        ></div>
      </div>

      <div class="absolute inset-0 bg-linear-to-b from-slate-900/30 to-slate-900/50 pointer-events-none"></div>

      <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 z-2 text-center text-white w-full px-8">
        <h1 class="text-5xl md:text-[3.5rem] font-bold tracking-wide mb-4 drop-shadow-[0_4px_12px_rgba(0,0,0,0.3)]">
          YOUR NEXT ADVENTURE
        </h1>
        <p class="text-xl md:text-[1.3rem] opacity-95 drop-shadow-[0_2px_8px_rgba(0,0,0,0.3)]">
          Explore thousands of islands, infinite memories
        </p>
      </div>

      <!-- Carousel Controls -->
      <button
        @click="prevSlide"
        class="absolute top-1/2 left-8 -translate-y-1/2 z-3 w-12 h-12 md:w-[50px] md:h-[50px] rounded-full bg-white/20 border-2 border-white/60 text-white text-4xl md:text-[2.5rem] cursor-pointer transition-all duration-300 flex items-center justify-center backdrop-blur-sm hover:bg-white/30 hover:border-white/80 hover:scale-110 md:left-8"
      ></button>
      <button
        @click="nextSlide"
        class="absolute top-1/2 right-8 -translate-y-1/2 z-3 w-12 h-12 md:w-[50px] md:h-[50px] rounded-full bg-white/20 border-2 border-white/60 text-white text-4xl md:text-[2.5rem] cursor-pointer transition-all duration-300 flex items-center justify-center backdrop-blur-sm hover:bg-white/30 hover:border-white/80 hover:scale-110 md:right-8"
      ></button>
      <!-- Carousel Indicators -->
      <div class="absolute bottom-12 left-1/2 -translate-x-1/2 z-2 flex gap-3">
        <button
          v-for="(image, index) in carouselImages"
          :key="index"
          @click="goToSlide(index)"
          class="w-3 h-3 rounded-full bg-white/50 border-2 border-white/80 cursor-pointer transition-all duration-300 p-0 hover:bg-white/70 hover:scale-125"
          :class="{ 'bg-white! w-8! rounded-md!': currentSlide === index }"
        ></button>
      </div>
    </section>

    <!-- NATURE SECTION -->
    <section id="nature" class="py-16 bg-linear-to-br from-green-400 via-green-300 to-green-100/80 scroll-mt-20">
      <div class="max-w-[1120px] mx-auto px-6">
        <div class="text-center mb-12">
          <span class="inline-block text-xs uppercase tracking-[0.9em] text-white/100 font-semibold mb-4">
            NATURE
          </span>
          <h2 class="text-4xl font-bold text-slate-900 mb-3 tracking-tight">
            Nikmati Keindahan Alam Indonesia
          </h2>
          <p class="text-base text-slate-600 leading-relaxed max-w-[700px] mx-auto">
            Jelajahi keajaiban alam Indonesia yang masih asri dan mempesona
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-7">
          <article
            v-for="(nature, i) in natureDestinations"
            :key="i"
            class="bg-white rounded-2xl overflow-hidden shadow-[0_4px_12px_rgba(0,0,0,0.08)] transition-all duration-250 hover:-translate-y-1.5 hover:shadow-[0_10px_26px_rgba(0,0,0,0.15)]"
          >
            <div class="relative w-full h-[150px] overflow-hidden">
              <img
                :src="nature.image"
                :alt="nature.name"
                class="w-full h-full object-cover transition-transform duration-500 hover:scale-110"
              />
              <div class="absolute inset-0 bg-linear-to-b from-black/10 to-black/35"></div>
              <div class="absolute bottom-3 left-3.5 z-2 text-white text-xs font-medium bg-black/55 px-3 py-1.5 rounded-full backdrop-blur-sm">
                <span>📍 {{ nature.location }}</span>
              </div>
            </div>
            <div class="px-5 pt-4 pb-5">
              <h3 class="text-lg font-bold text-slate-900 mb-1.5">{{ nature.name }}</h3>
              <p class="text-slate-600 leading-relaxed mb-3.5 text-sm">{{ nature.description }}</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- SUN & BEACH SECTION -->
    <section id="beach" class="py-16 bg-linear-to-br from-amber-400 via-amber-300 to-sky-200/80 scroll-mt-20">
      <div class="max-w-[1120px] mx-auto px-6">
        <div class="text-center mb-12">
          <span class="inline-block text-xs uppercase tracking-[0.9em] text-white/100 font-semibold mb-4">
            SUN & BEACH
          </span>
          <h2 class="text-4xl font-bold text-slate-900 mb-3 tracking-tight">
            Rasakan Kehangatan Pantai Tropis
          </h2>
          <p class="text-base text-slate-600 leading-relaxed max-w-[700px] mx-auto">
            Nikmati pesona pantai-pantai eksotis dengan pasir putih dan air laut jernih
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-7">
          <article
            v-for="(beach, i) in beachDestinations"
            :key="i"
            class="bg-white rounded-xl overflow-hidden shadow-[0_2px_8px_rgba(0,0,0,0.06)] transition-all duration-300 hover:-translate-y-1.5 hover:shadow-[0_10px_28px_rgba(0,0,0,0.12)]"
          >
            <div class="relative w-full h-[200px] overflow-hidden">
              <img
                :src="beach.image"
                :alt="beach.name"
                class="w-full h-full object-cover transition-transform duration-500 hover:scale-110"
              />
              <div class="absolute inset-0 bg-linear-to-b from-black/10 to-black/35"></div>
              <div class="absolute bottom-3 left-3 z-2 text-white text-xs font-medium bg-black/45 px-3 py-1.5 rounded-full backdrop-blur-sm">
                <span>📍 {{ beach.location }}</span>
              </div>
            </div>
            <div class="px-5 pt-4 pb-5">
              <h3 class="text-lg font-bold text-slate-900 mb-1.5">{{ beach.name }}</h3>
              <p class="text-slate-600 leading-relaxed mb-3.5 text-sm">{{ beach.description }}</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- HIGHLAND SECTION -->
    <section id="highland" class="py-16 bg-linear-to-br from-sky-400 via-sky-300 to-sky-200/80 scroll-mt-20">
      <div class="max-w-[1120px] mx-auto px-6">
        <div class="text-center mb-12">
          <span class="inline-block text-xs uppercase tracking-[0.9em] text-white/100 font-semibold mb-4">
            HIGHLAND
          </span>
          <h2 class="text-4xl font-bold text-slate-900 mb-3 tracking-tight">
            Jelajahi Dataran Tinggi yang Menakjubkan
          </h2>
          <p class="text-base text-slate-600 leading-relaxed max-w-[700px] mx-auto">
            Rasakan udara sejuk dan pemandangan spektakuler di dataran tinggi Indonesia
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-7">
          <article
            v-for="(highland, i) in highlandDestinations"
            :key="i"
            class="bg-white rounded-xl overflow-hidden shadow-[0_2px_8px_rgba(0,0,0,0.06)] transition-all duration-300 hover:-translate-y-1.5 hover:shadow-[0_10px_28px_rgba(0,0,0,0.12)]"
          >
            <div class="relative w-full h-[200px] overflow-hidden">
              <img
                :src="highland.image"
                :alt="highland.name"
                class="w-full h-full object-cover transition-transform duration-500 hover:scale-110"
              />
              <div class="absolute inset-0 bg-linear-to-b from-black/10 to-black/35"></div>
              <div class="absolute bottom-3 left-3 z-2 text-white text-xs font-medium bg-black/45 px-3 py-1.5 rounded-full backdrop-blur-sm">
                <span>📍 {{ highland.location }}</span>
              </div>
            </div>
            <div class="px-5 pt-4 pb-5">
              <h3 class="text-lg font-bold text-slate-900 mb-1.5">{{ highland.name }}</h3>
              <p class="text-slate-600 leading-relaxed mb-3.5 text-sm">{{ highland.description }}</p>
            </div>
          </article>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>

</style>