<script setup>
import { reactive, ref, computed } from "vue";
import { useDisplay } from "vuetify";
import emailjs from "@emailjs/browser";
import Swal from "sweetalert2";

const { xs } = useDisplay();

const loadingForm = ref(false);
const sentMessage = ref(false);

const formData = reactive({
  message: "",
  phone: "",
  name: "",
  email: "",
});

const cleanForm = () => {
  formData.name = "";
  formData.email = "";
  formData.phone = "";
  formData.message = "";
  loadingForm.value = false;
};

const isFormValid = computed(() => {
  return (
    formData.name !== "" &&
    formData.email !== "" &&
    formData.phone !== "" &&
    formData.message !== ""
  );
});

const handleSubmit = () => {
  loadingForm.value = true;
  emailjs
    .send(
      "service_57cec8c", // SERVICE ID
      "template_gf3u1n9", // TEMPLATE ID
      formData,
      "66edDB1GVsv4zq1Gw" // USER ID/PUBLIC KEY
    )
    .then(
      (response) => {
        console.log(response.status);
        loadingForm.value = false;
        cleanForm();
        Swal.fire({
          position: xs.value ? "bottom" : "bottom-end",
          icon: "success",
          text: "¡Mensaje enviado con éxito!",
          showConfirmButton: false,
          timer: 2500,
          backdrop: false,
          customClass: {
            popup: "containerSweetAlert",
            icon: "iconSweetAlert",
            htmlContainer: "htmlContainerSweetAlert",
          },
        });
        sentMessage.value = true;
      },
      () => {
        loadingForm.value = false;
        Swal.fire({
          position: xs.value ? "bottom" : "bottom-end",
          icon: "error",
          text: "Ocurrió un error al enviar el mensaje.",
          showConfirmButton: false,
          timer: 2500,
          backdrop: false,
          customClass: {
            popup: "containerSweetAlert",
            icon: "iconSweetAlert",
            htmlContainer: "htmlContainerSweetAlert",
          },
        });
      }
    );
};
</script>

<template>
  <section id="contacto" class="contact-section">
    <v-container class="relative z-10">
      <!-- Header -->
      <div class="text-center mb-16">
        <v-chip color="white" variant="tonal" class="mb-4"> Contacto </v-chip>

        <h2 class="contact-title mb-4 text-white">
          Ponte en contacto con nosotros
        </h2>

        <p class="contact-subtitle text-white">
          ¿Tienes alguna pregunta? Estamos aquí para ayudarte
        </p>
      </div>

      <v-row class="max-width">
        <!-- Info cards -->
        <v-col cols="12" lg="4">
          <div class="d-flex flex-column ga-6">
            <div
              v-for="(item, i) in [
                {
                  icon: 'mdi-phone',
                  title: 'Teléfono',
                  content: '(662) 110 1688',
                  link: 'tel:+526621101688',
                },
                {
                  icon: 'mdi-email',
                  title: 'Email',
                  content: 'tambos@hotmail.com',
                  link: 'mailto:tambos@hotmail.com',
                },
                {
                  icon: 'mdi-map-marker',
                  title: 'Dirección',
                  content:
                    'Av. Francisco Pirilares Lote 6 Manzana 118. Hermosillo, Sonora, México',
                },
              ]"
              :key="i"
              class="info-card"
            >
              <div class="info-icon">
                <v-icon :icon="item.icon" size="24" color="white" />
              </div>

              <h3 class="info-title">{{ item.title }}</h3>

              <a v-if="item.link" :href="item.link" class="info-text">
                {{ item.content }}
              </a>

              <p v-else class="info-text" style="white-space: pre-line">
                {{ item.content }}
              </p>
            </div>
          </div>
        </v-col>

        <!-- Form -->
        <v-col cols="12" lg="8">
          <v-card class="form-card">
            <v-form @submit.prevent="handleSubmit">
              <v-row>
                <v-col cols="12" md="6">
                  <h4 class="mb-2 text-grey-darken-3">Nombre completo</h4>
                  <v-text-field
                    v-model="formData.name"
                    placeholder="Tu nombre"
                    variant="outlined"
                    rounded="xl"
                    single-line
                    required
                  />
                </v-col>

                <v-col cols="12" md="6">
                  <h4 class="mb-2 text-grey-darken-3">Correo electrónico</h4>
                  <v-text-field
                    v-model="formData.email"
                    placeholder="tu@email.com"
                    type="email"
                    variant="outlined"
                    rounded="xl"
                    single-line
                    required
                  />
                </v-col>
              </v-row>

              <h4 class="mb-2 text-grey-darken-3">Teléfono</h4>
              <v-text-field
                v-model="formData.phone"
                v-mask="'(###) ###-####'"
                placeholder="+52 555 123 4567"
                variant="outlined"
                single-line
                rounded="xl"
              />

              <h4 class="mb-2 text-grey-darken-3">Mensaje</h4>
              <v-textarea
                v-model="formData.message"
                placeholder="¿En qué podemos ayudarte?"
                rows="5"
                variant="outlined"
                rounded="xl"
                single-line
                required
              />

              <v-btn
                type="submit"
                color="#00996c"
                size="x-large"
                rounded="xl"
                class="text-none font-weight-bold"
                :disabled="!isFormValid"
                :loading="loadingForm"
                block
                append-icon
                flat
              >
                Enviar mensaje
                <v-icon class="ml-2" icon="mdi-send" size="16" color="white" />
              </v-btn>
            </v-form>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
.contact-section {
  position: relative;
  padding: 120px 0;
  overflow: hidden;
  background: linear-gradient(to bottom right, #059669, #0d9488, #06b6d4);
}

.contact-title {
  font-size: clamp(2.5rem, 4vw, 3rem);
  font-weight: 700;
  color: white;
}

.contact-subtitle {
  font-size: 1.125rem;
  color: rgba(255, 255, 255, 0.9);
  max-width: 640px;
  margin: 0 auto;
}

/* Info cards */
.info-card {
  background: rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(12px);
  border-radius: 20px;
  padding: 24px;
  border: 1px solid rgba(255, 255, 255, 0.25);
  transition: all 0.3s ease;
}

.info-card:hover {
  background: rgba(255, 255, 255, 0.2);
}

.info-icon {
  width: 48px;
  height: 48px;
  border-radius: 14px;
  background: rgba(255, 255, 255, 0.25);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 16px;
}

.info-title {
  color: white;
  font-weight: 600;
  margin-bottom: 8px;
}

.info-text {
  color: rgba(255, 255, 255, 0.85);
}

/* Form */
.form-card {
  padding: 32px;
  border-radius: 24px;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
</style>
