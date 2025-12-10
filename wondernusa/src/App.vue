<script setup>
import { RouterView } from 'vue-router'

import Navbar from './components/headerfooter/Navbar.vue'
import FooterSection from './components/headerfooter/Footer.vue'
</script>

<template>
  <Navbar />
  <RouterView />
  <FooterSection />
</template>
