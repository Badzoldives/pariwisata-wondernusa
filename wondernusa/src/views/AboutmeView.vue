<script setup>
import { ref } from 'vue'

const imageAbout = '/src/assets/hero-makassar.jpg'
const testimonials = ref([
  {
    title: 'Skill 1',
    text: "Lorem ipsum",
    author: "Tim Wondernusa"
  },
  {
    title: 'Skill 2',
    text: "Lorem ipsum.",
    author: "Tim Wondernusa"
  },
  {
    title: 'Skill 3',
    text: "Lorem ipsum.",
    author: "Tim Wondernusa"
  }
])
</script>

<template>
  <div class="min-h-screen text-slate-900 bg-linear-to-b from-[#cfe8ff] to-[#b7dfff] pt-[50px] font-sans"
       style="background-image: radial-gradient(rgba(255,255,255,0.06) 1px, transparent 1px), linear-gradient(180deg, rgba(255,255,255,0.02), transparent); background-size: 20px 20px, cover;">

    <!-- ABOUT COPY BELOW -->
    <section class="bg-gradient-to-b from-sky-200 to-white mx-auto px-5 py-32 text-center">
      <div class="max-w-3xl mx-auto">
        <h2 class="text-4xl mb-2.5 font-bold text-[#06263a]">Eka Purnamasari Arfat</h2>
        <p class="text-[rgba(6,38,58,0.8)] leading-[1.8]">
          Eka Purnamasari Arfat-11231022-Informatika
        </p>
      </div>
    </section>

    <!-- MAIN ABOUT LAYOUT -->
    <main class="pb-8">
      <div class="max-w-5xl mx-auto px-5 grid grid-cols-1 lg:grid-cols-2 gap-10 items-center">
        <!-- Left: Testimonials -->
        <div class="py-8 lg:py-10 flex justify-center">
          <div class="flex flex-col items-center gap-6 max-w-[640px]">
            <article
              v-for="(t, i) in testimonials"
              :key="i"
              class="bg-linear-to-b from-[rgba(255,255,255,0.04)] to-[rgba(255,255,255,0.02)] rounded-lg p-[1.4rem_1.6rem] shadow-[0_6px_18px_rgba(2,6,23,0.06)]"
              style="backdrop-filter: blur(2px);">
              <h3 class="text-[1.05rem] tracking-[0.18em] uppercase text-[rgba(6,38,58,0.95)] mb-2.5">
                {{ t.title }}
              </h3>
              <p class="text-[rgba(6,38,58,0.85)] leading-[1.7] text-[0.95rem] mb-3.5">
                {{ t.text }}
              </p>
              <div class="text-[rgba(6,38,58,0.7)] italic text-[0.88rem]">
                / {{ t.author }}
              </div>
            </article>
          </div>
        </div>

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

        <!-- Right: foto -->
        <div class="flex items-center justify-center order-2 lg:order-none mt-4 lg:mt-0">
          <div class="w-full h-[260px] md:h-[360px] lg:h-[420px] rounded-xl overflow-hidden shadow-[0_18px_40px_rgba(2,6,23,0.18)] relative bg-linear-to-br from-[#ffffff33] to-[#e6f5ff33] group">
            <img
              :src="imageAbout"
              alt="About image"
              class="w-full h-full object-cover block origin-center transition-transform duration-600 ease-in-out group-hover:scale-105" />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>
