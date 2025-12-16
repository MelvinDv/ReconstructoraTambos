<script setup>
import heroBg from "../assets/heroBg.jpg";
</script>

<template>
  <section id="inicio" class="hero">
    <!-- Background -->
    <v-img :src="heroBg" cover class="hero-bg">
      <!-- Overlay -->
      <div class="hero-overlay"></div>
    </v-img>

    <!-- Content -->
    <v-container class="hero-content">
      <v-row>
        <v-col cols="12" md="8">
          <!-- Badge -->
          <v-chip color="#00996c" variant="tonal" class="mb-6">
            Reconstructora de tambos
          </v-chip>

          <!-- Title -->
          <h1 class="hero-title mb-6">
            Líderes en Reconstructora de
            <span class="gradient-text">Tambos</span>
          </h1>

          <!-- Subtitle -->
          <p class="hero-subtitle mb-8">
            Planta de reconstrucción y manejo de tambos residuales, asi como la
            recoleccion, transportación, acopio, disposicion final de todo tipo
            de residuos de manejo especial, contamos también con el servicio de
            destrucciones fiscales.
          </p>

          <!-- Actions -->
          <div class="d-flex flex-column flex-sm-row ga-4 mb-12">
            <v-btn
              class="text-none"
              color="#00977a"
              size="x-large"
              rounded="xl"
              href="#servicios"
              append-icon
            >
              Ver Servicios
            </v-btn>

            <v-btn
              class="text-none"
              variant="outlined"
              color="white"
              size="x-large"
              rounded="xl"
              href="#contacto"
            >
              Contactar
            </v-btn>
          </div>

          <!-- Features -->
          <v-row>
            <v-col cols="12" sm="4" class="d-flex align-center ga-3">
              <v-icon color="#00977a" size="28"
                >mdi-check-decagram-outline</v-icon
              >
              <span class="text-white">Calidad garantizada</span>
            </v-col>

            <v-col cols="12" sm="4" class="d-flex align-center ga-3">
              <v-icon color="#00977a" size="28"
                >mdi-check-decagram-outline</v-icon
              >
              <span class="text-white">Envío nacional</span>
            </v-col>

            <v-col cols="12" sm="4" class="d-flex align-center ga-3">
              <v-icon color="#00977a" size="28"
                >mdi-check-decagram-outline</v-icon
              >
              <span class="text-white">Años de experiencia</span>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>

    <!-- Decorative fade -->
    <div class="hero-fade"></div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  padding-top: 100px;
  padding-bottom: 140px;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to right,
    rgba(17, 24, 39, 0.95),
    rgba(17, 24, 39, 0.85),
    rgba(17, 24, 39, 0.7)
  );
}

.hero-content {
  position: relative;
  z-index: 2;
}

.hero-title {
  font-size: clamp(3rem, 5vw, 4.5rem);
  font-weight: 700;
  color: white;
  line-height: 1.1;
}

.gradient-text {
  background: linear-gradient(to right, #34d399, #2dd4bf);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  font-size: 1.25rem;
  color: #d1d5db;
  max-width: 720px;
  line-height: 1.7;
}

.hero-fade {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 96px;
  background: linear-gradient(to top, white, transparent);
  z-index: 3;
}
</style>
