<script setup>
import logo from "../assets/logo.png";

const currentYear = new Date().getFullYear();
</script>

<template>
  <footer class="footer">
    <v-container>
      <!-- Top grid -->
      <v-row class="mb-12">
        <!-- Company -->
        <v-col cols="12" md="6" lg="3">
          <div class="brand">
            <v-img
              :src="logo"
              alt="Logo Reestructuradora de Tanques"
              max-width="200px"
            />
          </div>

          <p class="footer-text text-justify">
            Planta de reconstrucción y manejo de tambos residuales, asi como la
            recoleccion, transportación, acopio, disposicion final de todo tipo
            de residuos de manejo especial, contamos también con el servicio de
            destrucciones fiscales.
          </p>

          <div class="socials">
            <v-btn icon class="social-btn"
              ><v-icon color="white" icon="mdi-facebook"
            /></v-btn>
            <v-btn icon class="social-btn"
              ><v-icon color="white" icon="mdi-whatsapp"
            /></v-btn>
            <v-btn icon class="social-btn"
              ><v-icon icon="mdi-youtube" color="white"
            /></v-btn>
          </div>
        </v-col>

        <!-- Links -->
        <v-col cols="12" md="6" lg="3">
          <h4 class="footer-title">Enlaces Rápidos</h4>
          <ul class="footer-list">
            <li><a href="#inicio">Inicio</a></li>
            <li><a href="#servicios">Servicios</a></li>
            <li><a href="#nosotros">Nosotros</a></li>
            <li><a href="#contacto">Contacto</a></li>
          </ul>
        </v-col>

        <!-- Services -->
        <v-col cols="12" md="6" lg="3">
          <h4 class="footer-title">Servicios</h4>
          <ul class="footer-list muted">
            <li>Reconstrucción de Tambos</li>
            <li>Destrucciones Fiscales</li>
            <li>Transporte de Escombros</li>
            <li>Transporte de Residuos</li>
          </ul>
        </v-col>

        <!-- Contact -->
        <v-col cols="12" md="6" lg="3">
          <h4 class="footer-title">Contacto</h4>
          <ul class="contact-list">
            <li>
              <v-icon icon="mdi-map-marker-outline" />
              <span>
                Av. Francisco Pirilares Lote 6 Manzana 118.<br />
                Hermosillo, Sonora, México
              </span>
            </li>
            <li>
              <v-icon icon="mdi-phone-outline" />
              <a href="tel:+5226221101688">+52 (662) 110 1688</a>
            </li>
            <li>
              <v-icon icon="mdi-email-outline" />
              <a href="mailto:tambos@hotmail.com"> tambos@hotmail.com </a>
            </li>
          </ul>
        </v-col>
      </v-row>

      <!-- Bottom bar -->
      <div class="footer-bottom">
        <p>
          © {{ currentYear }} Reconstructora de Tambos. Todos los derechos
          reservados.
        </p>

        <div class="footer-links d-none">
          <a href="#">Privacidad</a>
          <a href="#">Términos</a>
          <a href="#">Cookies</a>
        </div>
      </div>
    </v-container>
  </footer>
</template>

<style scoped>
.footer {
  background: #111827;
  color: white;
  padding: 80px 0 32px;
}

/* Brand */
.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

.brand-logo {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: linear-gradient(135deg, #059669, #0d9488);
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 20px;
}

.brand-title {
  font-weight: 600;
}

.brand-subtitle {
  font-size: 14px;
  color: #9ca3af;
}

.footer-text {
  color: #9ca3af;
  margin-bottom: 24px;
}

/* Socials */
.socials {
  display: flex;
  gap: 12px;
}

.social-btn {
  background: rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.social-btn:hover {
  background: #059669;
}

/* Titles */
.footer-title {
  font-weight: 600;
  margin-bottom: 24px;
}

/* Lists */
.footer-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-list li {
  margin-bottom: 12px;
}

.footer-list a {
  color: #9ca3af;
  text-decoration: none;
  transition: color 0.3s;
}

.footer-list a:hover {
  color: #34d399;
}

.footer-list.muted li {
  color: #9ca3af;
}

/* Contact */
.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.contact-list li {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  color: #9ca3af;
  margin-bottom: 16px;
}

.contact-list a {
  color: inherit;
  text-decoration: none;
}

.contact-list a:hover {
  color: #34d399;
}

/* Bottom */
.footer-bottom {
  border-top: 1px solid #1f2937;
  padding-top: 24px;
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  justify-content: space-between;
  align-items: center;
  color: #9ca3af;
  font-size: 14px;
}

.footer-links {
  display: flex;
  gap: 24px;
}

.footer-links a {
  color: #9ca3af;
  text-decoration: none;
}

.footer-links a:hover {
  color: #34d399;
}
</style>
