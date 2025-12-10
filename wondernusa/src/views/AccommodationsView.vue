<script setup>
import { ref, computed } from 'vue'

// Data destinasi untuk filter chips
const destinations = ['Semua', 'Bali', 'Makassar', 'Papua', 'Kupang', 'Sumba',]
const selectedDestination = ref('Bali')

const accommodations = [
  {
    id: 1,
    name: 'Grand Sunset Resort & Spa',
    city: 'Bali',
    rating: 4.8,
    price: 768000,
    imageUrl: 'https://images.unsplash.com/photo-1566073771259-6a8506099945?w=500&h=300&fit=crop'
  },
  {
    id: 2,
    name: 'Grand Sunset Resort & Spa',
    city: 'Bali',
    rating: 4.8,
    price: 768000,
    imageUrl: 'https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?w=500&h=300&fit=crop'
  },
  {
    id: 3,
    name: 'Losari Beach Hotel',
    city: 'Makassar',
    rating: 4.6,
    price: 550000,
    imageUrl: 'https://images.unsplash.com/photo-1571896349842-33c89424de2d?w=500&h=300&fit=crop'
  },
  {
    id: 4,
    name: 'Papua Paradise Eco Resort',
    city: 'Papua',
    rating: 4.9,
    price: 1200000,
    imageUrl: 'https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?w=500&h=300&fit=crop'
  },
  {
    id: 5,
    name: 'Aston Kupang Hotel',
    city: 'Kupang',
    rating: 4.5,
    price: 450000,
    imageUrl: 'https://images.unsplash.com/photo-1542314831-068cd1dbfeeb?w=500&h=300&fit=crop'
  },
  {
    id: 6,
    name: 'Sumba Nautil Resort',
    city: 'Sumba',
    rating: 4.7,
    price: 890000,
    imageUrl: 'https://images.unsplash.com/photo-1551882547-ff40c63fe5fa?w=500&h=300&fit=crop'
  }
]

// Computed filtered list berdasarkan destinasi terpilih
const filteredAccommodations = computed(() => {
  if (selectedDestination.value === 'Semua') {
    return accommodations
  }
  return accommodations.filter((acc) => acc.city === selectedDestination.value)
})

// Format harga ke Rupiah
function formatPrice(price) {
  return new Intl.NumberFormat('id-ID', {
    style: 'currency',
    currency: 'IDR',
    minimumFractionDigits: 0
  }).format(price)
}
</script>

<template>
  <div class="min-h-screen bg-slate-50 font-sans">
    <!-- HERO SECTION -->
    <section class="pt-32 pb-12 bg-linear-to-br from-sky-50 to-sky-100">
      <div class="max-w-7xl mx-auto px-6">
        <div class="text-center max-w-3xl mx-auto">
          <p class="text-xs tracking-[0.15em] uppercase text-slate-500 mb-3 font-semibold">
            ACCOMMODATIONS
          </p>
          <h1 class="text-4xl md:text-5xl font-bold text-slate-900 mb-3 leading-tight">
            Ayo Jelajah Nusantara!
          </h1>
          <p class="text-base text-slate-600 mb-8 leading-relaxed">
            Temukan tempat menginap terbaik untuk liburanmu di seluruh Indonesia
          </p>

          <!-- Filter Chips -->
          <div class="flex flex-wrap gap-3 justify-center mt-8">
            <button
              v-for="dest in destinations"
              :key="dest"
              :class="[
                'px-5 py-2 rounded-3xl border text-sm font-medium cursor-pointer transition-all duration-200',
                selectedDestination === dest
                  ? 'bg-linear-to-br from-cyan-500 to-cyan-600 text-white border-transparent font-semibold'
                  : 'bg-white text-slate-600 border-slate-200 hover:border-sky-500 hover:text-sky-500'
              ]"
              @click="selectedDestination = dest"
            >
              {{ dest }}
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- GRID KARTU AKOMODASI -->
    <section class="py-12 pb-16">
      <div class="max-w-7xl mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <article
            v-for="acc in filteredAccommodations"
            :key="acc.id"
            class="bg-white rounded-2xl overflow-hidden shadow-sm border border-slate-100 transition-all duration-300 cursor-pointer hover:-translate-y-1 hover:shadow-xl"
          >
            <div class="w-full h-[200px] overflow-hidden bg-slate-200">
              <img 
                :src="acc.imageUrl" 
                :alt="acc.name" 
                class="w-full h-full object-cover transition-transform duration-400 hover:scale-105"
              />
            </div>
            <div class="p-5">
              <h3 class="text-lg font-semibold text-slate-900 mb-2">{{ acc.name }}</h3>
              <div class="flex justify-between items-center mb-3">
                <div class="flex items-center gap-1 text-sm text-slate-600">
                  <span class="text-sm">📍</span>
                  <span>{{ acc.city }}</span>
                </div>
                <div class="flex items-center gap-1 text-sm text-slate-600">
                  <span class="text-base text-yellow-400">★</span>
                  <span>{{ acc.rating }}</span>
                </div>
              </div>
              <div class="text-base font-bold text-slate-900">{{ formatPrice(acc.price) }}</div>
            </div>
          </article>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
/* Minimal custom styles if needed */
</style>