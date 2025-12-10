<script setup>
import { ref } from 'vue'

defineOptions({
  name: 'NavBar'
})

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<template>
  <header class="fixed top-0 left-0 right-0 h-[72px] flex items-center z-[100] bg-white/10 backdrop-blur-[20px] backdrop-saturate-[180%] border-b border-white/20 shadow-[0_8px_32px_rgba(0,0,0,0.08)] px-6 md:px-6">
    <div class="max-w-[1200px] mx-auto w-full flex items-center justify-between">
      <!-- Brand -->
      <div>
        <router-link
          to="/"
          @click="closeMobileMenu"
          class="font-bold tracking-[0.15em] uppercase text-slate-900 text-[1.1rem] md:text-base no-underline transition-colors duration-200 hover:text-sky-500"
        >
          Wondernusa
        </router-link>
      </div>

      <!-- Desktop Menu -->
      <nav class="hidden md:flex gap-8 text-[0.9rem] font-semibold">
        <router-link
          to="/"
          class="text-slate-600 no-underline transition-colors duration-200 relative after:content-[''] after:absolute after:bottom-[-4px] after:left-0 after:w-0 after:h-[2px] after:bg-sky-500 after:transition-[width] after:duration-300 hover:text-sky-500 hover:after:w-full [&.router-link-active]:text-sky-500 [&.router-link-active]:after:w-full"
        >
          Home
        </router-link>
        <router-link
          to="/destinations"
          class="text-slate-600 no-underline transition-colors duration-200 relative after:content-[''] after:absolute after:bottom-[-4px] after:left-0 after:w-0 after:h-[2px] after:bg-sky-500 after:transition-[width] after:duration-300 hover:text-sky-500 hover:after:w-full [&.router-link-active]:text-sky-500 [&.router-link-active]:after:w-full"
        >
          Destinations
        </router-link>
        <router-link
          to="/accommodations"
          class="text-slate-600 no-underline transition-colors duration-200 relative after:content-[''] after:absolute after:bottom-[-4px] after:left-0 after:w-0 after:h-[2px] after:bg-sky-500 after:transition-[width] after:duration-300 hover:text-sky-500 hover:after:w-full [&.router-link-active]:text-sky-500 [&.router-link-active]:after:w-full"
        >
          Accommodations
        </router-link>
        <router-link
          to="/about"
          class="text-slate-600 no-underline transition-colors duration-200 relative after:content-[''] after:absolute after:bottom-[-4px] after:left-0 after:w-0 after:h-[2px] after:bg-sky-500 after:transition-[width] after:duration-300 hover:text-sky-500 hover:after:w-full [&.router-link-active]:text-sky-500 [&.router-link-active]:after:w-full"
        >
          About Us
        </router-link>
        <router-link
          to="/contact"
          class="text-slate-600 no-underline transition-colors duration-200 relative after:content-[''] after:absolute after:bottom-[-4px] after:left-0 after:w-0 after:h-[2px] after:bg-sky-500 after:transition-[width] after:duration-300 hover:text-sky-500 hover:after:w-full [&.router-link-active]:text-sky-500 [&.router-link-active]:after:w-full"
        >
          Contact
        </router-link>
      </nav>

      <!-- Mobile Hamburger Button -->
      <button
        @click="toggleMobileMenu"
        aria-label="Toggle menu"
        class="md:hidden bg-transparent border-none cursor-pointer p-2 z-[110]"
      >
        <span class="flex flex-col gap-[5px] w-[26px] h-[20px] relative">
          <span
            class="block w-full h-[3px] bg-slate-900 rounded-[3px] transition-all duration-300 ease-in-out"
            :class="{ 'rotate-45 translate-x-[7px] translate-y-[7px]': isMobileMenuOpen }"
          ></span>
          <span
            class="block w-full h-[3px] bg-slate-900 rounded-[3px] transition-all duration-300 ease-in-out"
            :class="{ 'opacity-0': isMobileMenuOpen }"
          ></span>
          <span
            class="block w-full h-[3px] bg-slate-900 rounded-[3px] transition-all duration-300 ease-in-out"
            :class="{ '-rotate-45 translate-x-[7px] -translate-y-[7px]': isMobileMenuOpen }"
          ></span>
        </span>
      </button>
    </div>

    <!-- Mobile Menu Overlay -->
    <transition
      enter-active-class="transition-all duration-300 ease-in-out"
      leave-active-class="transition-all duration-250 ease-in-out"
      enter-from-class="translate-x-full opacity-0"
      leave-to-class="translate-x-full opacity-0"
    >
      <nav
        v-if="isMobileMenuOpen"
        class="fixed top-[72px] right-0 w-[280px] h-[calc(100vh-72px)] bg-white/98 backdrop-blur-[20px] shadow-[-4px_0_24px_rgba(0,0,0,0.1)] p-8 px-6 flex flex-col gap-6 z-[105]"
      >
        <router-link
          to="/"
          @click="closeMobileMenu"
          class="text-slate-900 no-underline text-[1.1rem] font-semibold py-3 px-4 rounded-lg transition-all duration-200 hover:bg-sky-500/10 hover:text-sky-500 [&.router-link-active]:bg-sky-500/10 [&.router-link-active]:text-sky-500"
        >
          Home
        </router-link>
        <router-link
          to="/destinations"
          @click="closeMobileMenu"
          class="text-slate-900 no-underline text-[1.1rem] font-semibold py-3 px-4 rounded-lg transition-all duration-200 hover:bg-sky-500/10 hover:text-sky-500 [&.router-link-active]:bg-sky-500/10 [&.router-link-active]:text-sky-500"
        >
          Destinations
        </router-link>
        <router-link
          to="/accommodations"
          @click="closeMobileMenu"
          class="text-slate-900 no-underline text-[1.1rem] font-semibold py-3 px-4 rounded-lg transition-all duration-200 hover:bg-sky-500/10 hover:text-sky-500 [&.router-link-active]:bg-sky-500/10 [&.router-link-active]:text-sky-500"
        >
          Accommodations
        </router-link>
        <router-link
          to="/about"
          @click="closeMobileMenu"
          class="text-slate-900 no-underline text-[1.1rem] font-semibold py-3 px-4 rounded-lg transition-all duration-200 hover:bg-sky-500/10 hover:text-sky-500 [&.router-link-active]:bg-sky-500/10 [&.router-link-active]:text-sky-500"
        >
          About Us
        </router-link>
        <router-link
          to="/contact"
          @click="closeMobileMenu"
          class="text-slate-900 no-underline text-[1.1rem] font-semibold py-3 px-4 rounded-lg transition-all duration-200 hover:bg-sky-500/10 hover:text-sky-500 [&.router-link-active]:bg-sky-500/10 [&.router-link-active]:text-sky-500"
        >
          Contact
        </router-link>
      </nav>
    </transition>

    <!-- Mobile Menu Backdrop -->
    <transition
      enter-active-class="transition-opacity duration-300"
      leave-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      leave-to-class="opacity-0"
    >
      <div
        v-if="isMobileMenuOpen"
        @click="closeMobileMenu"
        class="fixed top-[72px] left-0 right-0 bottom-0 bg-black/30 z-[104]"
      ></div>
    </transition>
  </header>
</template>

