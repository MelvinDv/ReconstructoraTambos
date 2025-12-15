<script setup>
import aboutImg from "../assets/recoleccion.jpg";

const stats = [
  { icon: "mdi-medal-outline", value: "20+", label: "Años de experiencia" },
  {
    icon: "mdi-account-multiple",
    value: "500+",
    label: "Clientes satisfechos",
  },
  { icon: "mdi-shield-outline", value: "100%", label: "Calidad garantizada" },
  { icon: "mdi-chart-line-variant", value: "98%", label: "Satisfacción" },
];
</script>

<template>
  <section id="nosotros" class="about-section">
    <v-container>
      <v-row align="center" class="ga-12 ga-lg-20">
        <!-- Image column -->
        <v-col cols="12" lg="5">
          <div class="image-wrapper">
            <v-img :src="aboutImg" height="500" cover class="about-image">
              <div class="image-overlay" />
            </v-img>

            <!-- Floating card -->
            <div class="floating-card">
              <div class="d-flex align-center ga-4">
                <div class="floating-icon">
                  <v-icon icon="mdi-shield-outline" size="24" color="white" />
                </div>

                <div>
                  <p class="floating-value">100%</p>
                  <p class="floating-label">Garantía de calidad</p>
                </div>
              </div>
            </div>
          </div>
        </v-col>

        <!-- Content column -->
        <v-col cols="12" lg="6">
          <v-chip color="#00996c" variant="tonal" class="mb-4">
            Sobre Nosotros
          </v-chip>

          <h2 class="about-title mb-6">
            Bienvenidos a
            <span class="gradient-text"> Reconstructora de Tambos </span>
          </h2>

          <p class="about-text mb-6">
            Reconstructora de Tambos es una empresa autorizada y asegurada para
            el transporte y manejo de residuos, con permisos de CEDES, SEMARNAT
            y SCT. Cuenta con infraestructura, equipamiento y personal
            capacitado para brindar servicios ambientales integrales a
            industrias, comercios, minería y talleres, atendiendo tanto a
            pequeños como grandes generadores de residuos. Además, asesora a sus
            clientes para cumplir con la normativa vigente y ofrece
            administración y segregación de residuos de manejo especial (RME),
            garantizando reciclaje óptimo bajo estándares de seguridad, higiene
            y responsabilidad ecológica.
          </p>

          <!-- Stats -->
          <v-row class="mb-8">
            <v-col v-for="(stat, i) in stats" :key="i" cols="12" sm="6">
              <div class="stat-item">
                <div class="stat-icon">
                  <v-icon :icon="stat.icon" color="#00996c" size="20" />
                </div>

                <div>
                  <p class="stat-value">{{ stat.value }}</p>
                  <p class="stat-label">{{ stat.label }}</p>
                </div>
              </div>
            </v-col>
          </v-row>

          <!-- CTA -->
          <v-btn
            class="text-none"
            color="#00996c"
            size="x-large"
            rounded="xl"
            flat
            href="#contacto"
          >
            Contáctanos
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
.about-section {
  padding: 120px 0;
}

/* Image */
.image-wrapper {
  position: relative;
}

.about-image {
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(17, 24, 39, 0.6), transparent);
}

/* Floating card */
.floating-card {
  position: absolute;
  bottom: -24px;
  right: -24px;
  background: white;
  border-radius: 20px;
  padding: 24px;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  border: 1px solid #f3f4f6;
}

.floating-icon {
  width: 48px;
  height: 48px;
  border-radius: 999px;
  background: linear-gradient(to bottom right, #059669, #14b8a6);
  display: flex;
  align-items: center;
  justify-content: center;
}

.floating-value {
  font-size: 1.5rem;
  font-weight: 600;
  color: #111827;
}

.floating-label {
  font-size: 0.875rem;
  color: #6b7280;
}

/* Text */
.about-title {
  font-size: clamp(2.5rem, 4vw, 3rem);
  font-weight: 700;
  color: #111827;
}

.about-text {
  font-size: 1.125rem;
  color: #6b7280;
  line-height: 1.7;
}

/* Stats */
.stat-item {
  display: flex;
  gap: 12px;
}

.stat-icon {
  width: 40px;
  height: 40px;
  border-radius: 12px;
  background-color: #ecfdf5;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.stat-value {
  font-size: 1.5rem;
  font-weight: 600;
  color: #111827;
}

.stat-label {
  font-size: 0.875rem;
  color: #6b7280;
}

/* Gradient text */
.gradient-text {
  background: linear-gradient(to right, #059669, #14b8a6);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
