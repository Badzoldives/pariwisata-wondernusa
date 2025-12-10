<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const destinationCards = [
  {
    title: 'Nature',
    subtitle: 'Enjoy yourself with nature',
    image:
      'https://images.unsplash.com/photo-1559827260-dc66d52bef19?auto=format&fit=crop&w=800&q=80',
    link: '/destinations#nature'
  },
  {
    title: 'Sun & Beach',
    subtitle: 'Enjoy yourself with beach',
    image:
      'https://images.unsplash.com/photo-1500375592092-40eb2168fd21?auto=format&fit=crop&w=800&q=80',
    link: '/destinations#beach'
  },
  {
    title: 'Highland',
    subtitle: 'Explore highland destinations',
    image:
      'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=800&q=80',
    link: '/destinations#highland'
  }
]

// Carousel hero background
const heroImages = [
  '/src/assets/hero-makassar.jpg',
  'https://images.unsplash.com/photo-1555400038-63f5ba517a47?auto=format&fit=crop&w=1600&q=80',
  'https://images.unsplash.com/photo-1518837695005-2083093ee35b?auto=format&fit=crop&w=1600&q=80',
  'https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=1600&q=80'
]

const currentSlide = ref(0)
let carouselInterval = null


const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % heroImages.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + heroImages.length) % heroImages.length
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
  <div class="font-sans text-slate-900 bg-slate-100">

    <section id="home" class="relative min-h-[80vh] md:min-h-screen overflow-hidden">

      <div
        class="absolute inset-0 flex transition-transform duration-[800ms] ease-in-out"
        :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
      >
        <div
          v-for="(image, index) in heroImages"
          :key="index"
          class="relative min-w-full w-full h-full bg-cover bg-center bg-no-repeat brightness-100"
          :style="{ backgroundImage: `url(${image})` }"
        ></div>
      </div>

      <div class="flex items-center justify-center absolute inset-0 bg-[radial-gradient(circle_at_top,_rgba(15,23,42,0.4),_rgba(15,23,42,0.7))] z-10">

      <div class="relative z-20 h-[80vh] md:h-screen flex flex-col items-center justify-center text-center text-white max-w-6xl mx-auto px-6">
        <h1 class="font-sans text-5xl md:text-9xl font-bold uppercase tracking-widest drop-shadow-2xl">
          INDONESIA
        </h1>
        <p class="font-sans font-black mt-4 text-sm md:text-lg tracking-[0.3em] uppercase drop-shadow-md">
          Hidden Beauty of World
        </p>
        <router-link
          to="/destinations"
          class="mt-6 px-8 py-3 rounded-full bg-green-500 text-slate-900 text-xs font-semibold tracking-widest uppercase transition-all hover:bg-green-600 hover:-translate-y-0.5 shadow-lg hover:shadow-xl cursor-pointer inline-block no-underline">
          View Destinations
        </router-link>
      </div>

      <button
        class="hidden md:flex absolute top-1/2 left-8 -translate-y-1/2 z-20 bg-white/20 border-2 border-white/50 text-white text-4xl w-12 h-12 rounded-full items-center justify-center backdrop-blur cursor-pointer transition-all hover:bg-white/30 hover:scale-110"
        @click="prevSlide"
      ></button>

      <button
        class="hidden md:flex absolute top-1/2 right-8 -translate-y-1/2 z-20 bg-white/20 border-2 border-white/50 text-white text-4xl w-12 h-12 rounded-full items-center justify-center backdrop-blur cursor-pointer transition-all hover:bg-white/30 hover:scale-110"
        @click="nextSlide"
      ></button>

      <div class="absolute bottom-8 md:bottom-[120px] left-1/2 -translate-x-1/2 z-20 flex gap-3">
        <button
          v-for="(image, index) in heroImages"
          :key="index"
          class="w-3 h-3 rounded-full bg-white/50 border-2 border-white/80 cursor-pointer transition-all p-0 hover:bg-white/70 hover:scale-125"
          :class="{ '!bg-white !w-8 rounded-md': currentSlide === index }"
          @click="goToSlide(index)"
        ></button>
      </div>
    </div>

      <div class="absolute bottom-0 left-0 right-0 h-20 bg-gradient-to-t from-white to-transparent z-20"></div>
    </section>

    <section class="flex items-center justify-center bg-gradient-to-b from-white/95 via-[#fce4a8] to-[#fce4a8]">
        <div class="flex flex-col max-w-4xl mx-auto pt-16 text-center px-6 items-center text-xs tracking-[0.25em] text-sky-500 mb-6 font-['Raleway'] font-semibold">
          <h2 class="font-['Oswald'] text-[2.5rem] leading-[1.3] font-semibold text-slate-900 mb-8 tracking-wide uppercase">
            Selamat Datang di Indonesia!
          </h2>
          <div class="flex flex-col gap-2">
            <p class="font-['Montserrat'] text-base leading-[1.9] text-slate-600 mb-5 font-normal">
              Indonesia adalah negara kepulauan terbesar di dunia dengan keindahan alam yang memukau, budaya yang beragam, dan keramahan penduduknya. Dari pantai-pantai eksotis hingga
              gunung-gunung yang menjulang tinggi, setiap sudut Indonesia menyimpan keajaiban yang menunggu untuk dijelajahi.
            </p>
            <p class="font-['Montserrat'] text-base leading-[1.9] text-slate-600 mb-5 font-normal">
              Mari bersama kami menjelajahi destinasi-destinasi menakjubkan, merasakan pengalaman
              yang tak terlupakan, dan menciptakan kenangan indah di setiap perjalanan Anda.
            </p>
          </div>
        </div>
    </section>

    <section id="about" class="py-20 bg-gradient-to-t from-[#e0b23e] via-[#ffd771] to-[#fce4a8]">
      <div class="max-w-6xl mx-auto px-6 grid grid-cols-1 md:grid-cols-[1.1fr_1.3fr] gap-12 items-center">
        <div class="relative overflow-hidden rounded">
          <img
            class="w-full block rounded object-cover"
            src="https://images.unsplash.com/photo-1518548419970-58e3b4079ab2?auto=format&fit=crop&w=1000&q=80"
            alt="Kota di malam hari"
          />
          <div class="absolute left-3 bottom-3 md:left-0 md:bottom-6 bg-white px-5 py-2 md:px-6 md:py-2 font-bold text-base md:text-[1.4rem] tracking-widest uppercase shadow-lg">
            <span class="mr-1">ENJOY</span>
            <span class="font-extrabold">INDONESIA!</span>
          </div>
        </div>

        <div class="text-slate-900">
          <h2 class="font-['Cinzel'] text-[2.8rem] font-bold tracking-[0.15em] uppercase mb-6 text-slate-900 leading-[1.2]">
            ABOUT US
          </h2>

          <p class="font-['Montserrat'] text-base leading-[1.9] text-slate-600 mb-5 font-normal">
            Wondernusa adalah platform perjalanan yang membantu Anda mengeksplorasi
            keindahan Indonesia dengan cara yang lebih mudah dan menyenangkan.
            Kami mengkurasi destinasi, pengalaman, dan inspirasi perjalanan dari
            Sabang sampai Merauke.
          </p>
          <p class="font-['Montserrat'] text-base leading-[1.9] text-slate-600 mb-5 font-normal">
            Dengan menggabungkan informasi destinasi, rekomendasi aktivitas,
            serta nuansa visual yang hangat, kami ingin menemani setiap langkah
            Anda dalam merencanakan liburan yang berkesan.
          </p>
          <p class="font-['Montserrat'] text-base leading-[1.9] text-slate-600 mb-5 font-normal">
            Misi kami adalah menghadirkan pengalaman berwisata yang autentik,
            nyaman, dan penuh cerita, sekaligus memperkenalkan kekayaan alam
            dan budaya Indonesia kepada dunia.
          </p>

          <div class="mt-6 flex justify-start md:justify-end">
            <button class="bg-transparent border-none text-sm font-bold tracking-[0.2em] uppercase cursor-pointer relative group">
              DISCOVER
              <span class="absolute left-0 -bottom-1 w-full h-[1px] bg-slate-900 scale-x-0 group-hover:scale-x-100 transition-transform duration-200 origin-left"></span>
            </button>
          </div>
        </div>
      </div>
    </section>

    <section id="destinations" class="relative bg-slate-50 overflow-hidden">
      <div class="relative flex flex-col md:flex-row min-h-auto md:min-h-[600px]">

        <!-- Text Content (kiri) -->
        <div class="relative md:absolute left-0 top-0 bottom-0 w-full md:w-[45%] bg-transparent md:bg-gradient-to-r md:from-slate-50 md:via-slate-50/80 md:to-transparent z-20 flex items-center px-6 pt-8 md:p-0 md:pl-[5%]">
          <div class="max-w-full md:max-w-[420px] p-0 md:p-8">
            <div class="inline-flex items-center gap-2 font-['Raleway'] text-[0.7rem] font-bold uppercase tracking-[0.25em] text-slate-500 mb-4">
              <span class="text-base">✈</span>
              <span>WHERE TO GO?</span>
            </div>
            <h2 class="font-['Raleway'] text-[2.5rem] leading-[1.2] font-light text-slate-900 mb-6 tracking-wide">
              Pick your own journey.
            </h2>
            <p class="font-['Cormorant_Garamond'] text-base text-slate-500 leading-[1.7] font-normal mb-8">
              Jelajahi keindahan kepulauan Indonesia yang beragam, dari hamparan pasir putih bersih di pantai tropis hingga ketenangan berkabut di dataran tinggi yang megah.
            </p>
            <RouterLink
              to="/destinations"
              class="inline-block px-8 py-2.5 rounded-full border border-gray-300 bg-white text-slate-900 text-[0.85rem] font-medium tracking-widest uppercase cursor-pointer transition-all hover:bg-slate-900 hover:text-white hover:border-slate-900"
            >
              See All
            </RouterLink>
          </div>
        </div>

        <!-- Card scroll (kanan) -->
        <div class="flex-1 overflow-x-auto w-full scrollbar-hide">
          <div class="flex gap-8 px-6 pb-16 pt-8 md:pt-16 md:pl-[35%] md:pr-8 min-h-[400px] md:min-h-[600px] items-start md:items-center">
            <article
              v-for="(card, i) in destinationCards"
              :key="i"
              class="flex-none w-[300px] md:w-[420px] h-[400px] md:h-[500px] rounded-3xl overflow-hidden relative cursor-pointer transition-transform duration-300 hover:scale-[1.03] group"
            >
              <div class="w-full h-full relative">
                <img :src="card.image" :alt="card.title" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" />
              </div>
              <div class="absolute bottom-0 left-0 right-0 p-8 bg-gradient-to-t from-black/85 via-black/50 to-transparent text-white">
                <h3 class="font-['Raleway'] text-2xl font-bold text-white mb-3 tracking-wide">{{ card.title }}</h3>
                <p class="font-['Cormorant_Garamond'] text-base leading-[1.6] text-white/90 mb-4">{{ card.subtitle }}</p>
                <router-link
                  :to="card.link"
                  class="inline-block px-6 py-2 rounded-md border border-white/40 bg-transparent font-['Raleway'] text-[0.85rem] font-semibold tracking-widest uppercase text-white transition-all hover:bg-white/95 hover:text-slate-900 hover:border-white/95 no-underline">
                  Learn More
                </router-link>
              </div>
            </article>
          </div>
        </div>

      </div>
    </section>


  </div>
</template>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
    display: none;
}
.scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
</style>
