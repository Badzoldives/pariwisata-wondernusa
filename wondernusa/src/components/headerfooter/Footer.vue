<template>
  <footer class="bg-linear-to-br from-teal-700 to-teal-800 text-white pt-12 pb-6">
    <div class="max-w-7xl mx-auto px-6">
      <div class="grid grid-cols-1 md:grid-cols-[2fr_1fr_1fr] gap-8 mb-8">
      <!-- Brand Column -->
        <div class="flex flex-col gap-3">
          <h3 class="text-xl font-bold tracking-widest mb-2">WONDERNUSA</h3>
          <p class="text-sm leading-relaxed text-white/85">
          Wondernusa adalah platform perjalanan yang membantu Anda mengeksplorasi
          keindahan Indonesia dengan cara yang lebih mudah dan menyenangkan.
          </p>
          <div class="flex gap-4 mt-2">
            <a href="#" aria-label="Instagram" class="flex items-center justify-center w-8 h-8 bg-white/10 rounded-md text-white text-xs font-semibold transition-colors hover:bg-white/20">IG</a>
            <a href="#" aria-label="Facebook" class="flex items-center justify-center w-8 h-8 bg-white/10 rounded-md text-white text-xs font-semibold transition-colors hover:bg-white/20">FB</a>
            <a href="#" aria-label="WhatsApp" class="flex items-center justify-center w-8 h-8 bg-white/10 rounded-md text-white text-xs font-semibold transition-colors hover:bg-white/20">WA</a>
            <a href="#" aria-label="Twitter" class="flex items-center justify-center w-8 h-8 bg-white/10 rounded-md text-white text-xs font-semibold transition-colors hover:bg-white/20">X</a>
          </div>
        </div>

        <!-- Navigation Column -->
        <div class="flex flex-col gap-3">
          <h4 class="text-[0.95rem] font-semibold uppercase tracking-wider mb-2">Navigation</h4>
          <ul class="flex flex-col gap-2 p-0 m-0 list-none">
            <li><router-link to="/" class="text-white/85 text-sm hover:text-white transition-colors">Home</router-link></li>
            <li><router-link to="/destinations" class="text-white/85 text-sm hover:text-white transition-colors">Destinations</router-link></li>
            <li><router-link to="/accommodations" class="text-white/85 text-sm hover:text-white transition-colors">Accommodations</router-link></li>
            <li><router-link to="/about" class="text-white/85 text-sm hover:text-white transition-colors">About Us</router-link></li>
            <li><router-link to="/contact" class="text-white/85 text-sm hover:text-white transition-colors">Contact</router-link></li>
          </ul>
        </div>

        <!-- Contact Column -->
        <div class="flex flex-col gap-3">
          <h4 class="text-[0.95rem] font-semibold uppercase tracking-wider mb-2">Contact Us</h4>
          <address class="not-italic text-sm leading-relaxed text-white/85">
            <p class="my-1">Jl. Pelayaran No. 12, Balikpapan, Indonesia</p>
            <p class="my-1">+62 21 1234 5678</p>
            <p class="my-1">info@wondernusa.com</p>
          </address>
        </div>
      </div>
    </div>

    <!-- Copyright -->
    <div class="pt-8 border-t border-white/15 text-center">
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterSection'
}
</script>
