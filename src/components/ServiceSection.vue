<template>
  <section id="servicios" class="services-section">
    <v-container>
      <!-- Header -->
      <div class="text-center mb-16">
        <v-chip color="#00996c" variant="tonal" class="mb-4">
          Nuestros Servicios
        </v-chip>

        <h2 class="services-title mb-4">
          Lo que
          <span class="gradient-text">ofrecemos</span>
        </h2>

        <p class="services-subtitle">
          Servicios especializados en reconstrucción de tambos con el más alto
          estándar de calidad
        </p>
      </div>

      <!-- Grid -->
      <v-row>
        <v-col
          v-for="(service, i) in services"
          :key="i"
          cols="12"
          md="6"
          lg="3"
        >
          <v-card class="service-card" elevation="1">
            <!-- Icon -->
            <div class="icon-wrapper" :class="service.gradient">
              <v-icon :icon="service.icon" size="28" color="white" />
            </div>

            <h3 class="service-title">
              {{ service.title }}
            </h3>

            <p class="service-description">
              {{ service.description }}
            </p>

            <p class="verMas">Ver más</p>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
.services-section {
  padding: 120px 0;
  background-color: #f9fafb;
}

/* Header */
.services-title {
  font-size: clamp(2.5rem, 4vw, 3rem);
  font-weight: 700;
  color: #111827;
}

.services-subtitle {
  font-size: 1.125rem;
  color: #6b7280;
  max-width: 640px;
  margin: 0 auto;
}

/* Card */
.service-card {
  padding: 24px;
  border-radius: 20px;
  border: 1px solid #f3f4f6;
  transition: all 0.3s ease;
}

.service-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.15);
}

/* Icon */
.icon-wrapper {
  width: 56px;
  height: 56px;
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
  transition: transform 0.3s ease;
}

.service-card:hover .icon-wrapper {
  transform: scale(1.1);
}

/* Text */
.service-title {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 12px;
  color: #111827;
}

.service-description {
  color: #6b7280;
  line-height: 1.7;
}

.verMas {
  margin-top: 16px;
  font-weight: 600;
  color: #00996c;
  cursor: pointer;
}

/* Gradients */
.gradient-text {
  background: linear-gradient(to right, #059669, #14b8a6);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.gradient-blue {
  background: linear-gradient(to bottom right, #3b82f6, #06b6d4);
}

.gradient-green {
  background: linear-gradient(to bottom right, #10b981, #22c55e);
}

.gradient-orange {
  background: linear-gradient(to bottom right, #f97316, #ef4444);
}

.gradient-purple {
  background: linear-gradient(to bottom right, #8b5cf6, #ec4899);
}
</style>

<script setup>
const services = [
  {
    icon: "mdi-cup",
    title: "Tambos",
    description:
      "Reacondicionamos tambos y totes metálicos y de plástico para grandes volúmenes.",
    gradient: "gradient-blue",
  },
  {
    icon: "mdi-newspaper-remove",
    title: "Destrucciones Fiscales.",
    description:
      "Realizamos la destrucción fiscal de inventarios para deducir su costo en el ISR.",
    gradient: "gradient-green",
  },
  {
    icon: "mdi mdi-dump-truck",
    title: "Trasporte de escombros.",
    description:
      "Gestionamos los escombros desde su origen hasta la disposición final, entregando el manifiesto firmado y sellado.",
    gradient: "gradient-orange",
  },
  {
    icon: "mdi-delete-restore",
    title: "Transporte de residuos orgánicos.",
    description:
      "Colaboramos con la Planta Procesadora de Composta Granja Lux Sonorganic ",
    gradient: "gradient-purple",
  },
];
</script>
