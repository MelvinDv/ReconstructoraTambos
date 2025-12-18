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
      </div>

      <!-- Grid -->
      <v-row>
        <v-col
          v-for="(service, i) in services"
          :key="i"
          cols="12"
          md="6"
          lg="6"
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

            <span class="service-link" @click="openDialog(i)">
              Ver más <v-icon icon="mdi-arrow-right" size="18" />
            </span>
          </v-card>
        </v-col>
      </v-row>

      <v-card
        v-for="(info, index) of moreInfo"
        :key="index"
        rounded="xl"
        elevation="2"
        class="overflow-hidden mt-8"
      >
        <v-row no-gutters :class="{ 'flex-row-reverse': reverse }">
          <v-col cols="12" md="6">
            <v-img :src="info.image" height="100%" cover />
          </v-col>

          <v-col cols="12" md="6" class="pa-8 pa-md-12 d-flex align-center">
            <div>
              <v-chip color="teal" variant="tonal" class="mb-4">
                {{ info.tag }}
              </v-chip>

              <h3 class="text-h4 mb-4">
                {{ info.title }}
              </h3>

              <p class="text-body-1 text-medium-emphasis">
                {{ info.description }}
              </p>
            </div>
          </v-col>
        </v-row>
      </v-card>
    </v-container>

    <!-- Dialog -->
    <v-dialog v-model="dialogOpen" class="dialog-service" max-width="900">
      <v-card v-if="selectedService !== null" class="pa-4">
        <v-card-title class="dialog-header">
          <div class="dialog-icon" :class="services[selectedService].gradient">
            <v-icon :icon="services[selectedService].icon" />
          </div>
          {{ services[selectedService].title }}
          <v-spacer />
          <v-btn icon @click="closeDialog()" flat>
            <v-icon icon="mdi-close" />
          </v-btn>
        </v-card-title>

        <v-card-text class="dialog-body">
          <h3>Descripción</h3>
          <p v-html="services[selectedService].details.fullDescription"></p>

          <h4 v-if="services[selectedService].details.features.length > 0">
            Características
          </h4>
          <ul class="features">
            <li
              v-for="(f, i) in services[selectedService].details.features"
              :key="i"
            >
              <v-icon color="#00996c" icon="mdi-check-circle-outline" />
              {{ f }}
            </li>
          </ul>

          <h4 v-if="services[selectedService].details.benefits.length > 0">
            Beneficios
          </h4>
          <div class="benefits">
            <div
              v-for="(b, i) in services[selectedService].details.benefits"
              :key="i"
              class="benefit"
              :class="services[selectedService].gradient"
            >
              <v-icon icon="mdi-check" />
              {{ b }}
            </div>
          </div>

          <div
            v-for="(section, index) in services[selectedService].details
              .sections"
            :key="index"
            class="mt-6"
          >
            <h3 class="mt-4">{{ section.alt }}</h3>
            <p class="text-grey-darken-1 mb-2">{{ section.subtitle }}</p>

            <div v-if="section.type === 'image'" class="d-flex flex-wrap gap-4">
              <v-img
                v-for="(imgSrc, imgIndex) in section.src"
                :key="imgIndex"
                :src="imgSrc"
                :alt="section.alt"
                max-width="350"
              />
            </div>

            <div v-if="section.type === 'video'" class="d-flex flex-wrap gap-4">
              <video
                controls
                width="100%"
                v-for="(vidSrc, vidIndex) in section.src"
                :key="vidIndex"
              >
                <source :src="vidSrc" type="video/mp4" />
                Tu navegador no soporta videos
              </video>
            </div>
          </div>
        </v-card-text>

        <v-card-actions class="card-footer">
          <v-btn
            block
            class="text-none"
            style="background-color: #00996c"
            color="white"
            size="x-large"
            rounded="xl"
            flat
            @click="goToContact()"
          >
            Solicitar información
            <v-icon class="ml-2" right icon="mdi-arrow-right" />
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
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

.service-link {
  color: #059669;
  font-weight: 700;
  display: inline-flex;
  gap: 6px;
  align-items: center;
  transition: transform 0.3s ease;
}

.service-link:hover {
  color: #04724f;
  cursor: pointer;
}

.service-link:hover .v-icon {
  transform: translateX(4px);
  transition: transform 0.3s ease;
}

/* Dialog */
.dialog-service > .v-overlay__content > .v-card,
.v-dialog > .v-overlay__content > form > .v-card {
  border-radius: 24px;
}

.dialog-header {
  display: flex;
  align-items: center;
  gap: 12px;
  position: sticky;
  top: 0;
  background-color: white; /* o el color de tu card */
  z-index: 10;
  padding: 16px;
}

.dialog-icon {
  width: 48px;
  height: 48px;
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.dialog-body h4 {
  margin: 24px 0 12px;
}

.features {
  list-style: none;
  padding: 0;
}

.features li {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}

.benefits {
  display: grid;
  gap: 12px;
}

.benefit {
  background: #ecfdf5;
  padding: 12px 16px;
  border-radius: 12px;
  display: flex;
  gap: 8px;
  align-items: center;
}

.card-footer {
  position: sticky;
  bottom: 0;
  z-index: 10;
}
</style>

<script setup>
import { ref } from "vue";
import tamboMedidas from "../assets/tambos-medidas-249x300.jpg";
import tambosEspecificaciones from "../assets/tambos-especificaciones.jpg";
import ibcMedidas from "../assets/tanque-ibc-foto-249x300.jpg";
import ibcEspecificaciones from "../assets/tanque-ibc-especificaciones.jpg";
import dompe from "../assets/dompe.jpg";
import dompe2 from "../assets/dompe_2.jpg";
import transporteResiduos from "../assets/transporte_residuos.jpg";
import processo from "../assets/Proceso-de-recoleccion.jpg";
import videoDestruccion from "../assets/destrucciónFiscal.mp4";
import tambos from "../assets/tambos.png";

const dialogOpen = ref(false);
const selectedService = ref(null);

const openDialog = (i) => {
  selectedService.value = i;
  dialogOpen.value = true;
};

const closeDialog = () => {
  selectedService.value = null;
  dialogOpen.value = false;
};

const goToContact = () => {
  closeDialog();

  setTimeout(() => {
    window.location.href = "#contacto";
  }, 150);
};

const services = [
  {
    id: 1,
    icon: "mdi-cup",
    title: "Tambos",
    description:
      "Reacondicionamos tambos y totes metálicos y de plástico para grandes volúmenes.",
    gradient: "gradient-blue",
    details: {
      fullDescription: `
    <p class="mb-2">
      Reconstructora de Tambos no comercializa tambos usados de segunda mano. Nos especializamos en tambos reacondicionados, trabajados bajo estrictas autorizaciones ambientales y conforme a la normativa vigente.
    </p>
    <p class="mb-2">Nuestro compromiso es ofrecer productos:</p>
    <ul class="mb-2">
      <li>Libres de golpes, impurezas y etiquetas.</li>
      <li>Pintados en el color de su preferencia.</li>
      <li>Respaldados por un plan de manejo aprobado por CEDES.</li>
      </ul>
      <p class="mb-2">Además, somos <strong>coexportadores</strong> hacia Estados Unidos, Canadá y Europa, garantizando estándares de calidad internacional.</p>
      <p class="mb-2">La apariencia de nuestros tambos es prácticamente nueva, pero a un costo mucho más accesible.</p>
      <p style="color: #00996c; font-weight: 600">También compramos y vendemos tambos, totes, porrones y cubetas, brindando soluciones integrales para distintas necesidades industriales y comerciales.</p>
      `,
      sections: [
        {
          type: "image",
          src: [tamboMedidas, tambosEspecificaciones],
          alt: "Medidas Tambo 200 Litros",
          subtitle: "Especificaciones técnicas",
        },
        {
          type: "image",
          src: [ibcMedidas, ibcEspecificaciones],
          alt: "Tanque IBC de 1,000 Lts",
          subtitle: "Vehiculos disponibles",
        },
      ],
      features: [],
      benefits: [],
    },
  },
  {
    id: 2,
    icon: "mdi-newspaper-remove",
    title: "Destrucciones Fiscales.",
    description:
      "Realizamos la destrucción fiscal de inventarios para deducir su costo en el ISR.",
    gradient: "gradient-green",
    details: {
      fullDescription: `<p class="mb-2">La destrucción fiscal de inventarios es un procedimiento regulado por el SAT que permite eliminar productos sin valor comercial (caducos, dañados, obsoletos o excedentes) y deducir su costo en el Impuesto Sobre la Renta (ISR).</p>`,
      features: [
        "Cumplimiento con normativas fiscales y ambientales.",
        "Emisión de constancia de destrucción fiscal.",
        "Proceso seguro y documentado.",
        "Manejo responsable de residuos post-destrucción.",
        "Asesoría personalizada para optimizar beneficios fiscales.",
      ],
      benefits: [
        "Optimizar espacio y reducir costos de almacenamiento.",
        "Respaldar destrucciones fiscales mediante evidencia y certificación del proceso.",
      ],
      sections: [
        {
          type: "video",
          src: [videoDestruccion],
          alt: "Destrucción Fiscal",
          subtitle: "",
        },
      ],
    },
  },
  {
    id: 3,
    icon: "mdi mdi-dump-truck",
    title: "Trasporte de escombros.",
    description:
      "Gestionamos los escombros desde su origen hasta la disposición final, entregando el manifiesto firmado y sellado.",
    gradient: "gradient-orange",
    details: {
      fullDescription: `<p class=mb-2>El transporte de escombros es el servicio encargado de recolectar, trasladar y disponer de materiales sobrantes de construcciones, demoliciones o remodelaciones, garantizando un manejo seguro y conforme a la normativa ambiental.</p>`,
      features: [
        "Uso de vehículos especializados.",
        "Seguridad en el traslado.",
        "Flexibilidad de servicio.",
        "Destino autorizado.",
      ],
      benefits: [
        "Orden y limpieza en obra.",
        "Cumplimiento legal y ambiental.",
        "Optimización de tiempo y recursos.",
        "Entrega de manifiestos debidamente completados y sellados por los responsables de la cadena de custodia, garantizando el seguimiento hasta la disposición final.",
      ],
      sections: [
        {
          type: "image",
          src: [dompe, dompe2],
          alt: "Transporte de escombros",
          subtitle: "Especificaciones técnicas",
        },
      ],
    },
  },
  {
    id: 4,
    icon: "mdi-delete-restore",
    title: "Transporte de residuos orgánicos.",
    description:
      "Colaboramos con la Planta Procesadora de Composta Granja Lux Sonorganic ",
    gradient: "gradient-purple",
    details: {
      fullDescription: `<p class="mb-2">El transporte de residuos orgánicos consiste en la recolección y traslado de desechos biodegradables (restos de alimentos, podas, materiales vegetales) hacia sitios autorizados para su disposición final, como plantas de compostaje, biodigestores o rellenos sanitarios, asegurando un manejo seguro y sustentable.</p>`,
      features: [
        "Vehículos especializados.",
        "Rutas programadas.",
        "Seguridad sanitaria.",
        "Destino autorizado.",
      ],
      benefits: [
        "Reducción de impactos ambientales.",
        "Cumplimiento normativo.",
        "Aprovechamiento energético y agrícola.",
      ],
      sections: [
        {
          type: "image",
          src: [transporteResiduos],
          alt: "Transporte de residuos orgánicos",
          subtitle: "Vehículos",
        },
      ],
    },
  },
];

const moreInfo = [
  {
    tag: "Nuestro proceso",
    title: "Proceso de Recolección",
    description:
      "Contamos con un proceso estructurado en 4 pasos que garantiza calidad y eficiencia en cada etapa del servicio. Desde la recolección inicial hasta la entrega final, cada paso está diseñado para cumplir con los más altos estándares.",
    image: processo,
  },
  {
    tag: "Tambos",
    title: "Tambos de Alta Calidad",
    description:
      "Especializados en el reacondicionamiento de tambos metálicos y de plástico para grandes volúmenes. Nuestras instalaciones cumplen con todas las normativas de seguridad y calidad.",
    image: tambos,
  },
];
</script>
