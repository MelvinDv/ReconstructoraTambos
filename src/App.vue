<template>
  <v-app>
    <Navbar />
    <!-- Aquí va el resto de tu contenido -->
    <v-main>
      <v-container class="pa-0" fluid>
        <HeroSection />
        <ServiceSection />
        <About />
        <ContactSection />
        <FooterSection />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import HeroSection from "./components/HeroSection.vue";
import ServiceSection from "./components/ServiceSection.vue";
import About from "./components/About.vue";
import ContactSection from "./components/ContactSection.vue";
import FooterSection from "./components/FooterSection.vue";
</script>
