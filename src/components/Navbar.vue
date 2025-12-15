<template>
  <div>
    <!-- Barra superior verde -->
    <v-toolbar class="px-10" density="compact" color="#009875" dark>
      <div class="d-flex align-center justify-end" style="width: 100%">
        <v-icon start>mdi-phone</v-icon>
        <span class="me-4">Contacto</span>
        <v-icon start>mdi-email</v-icon>
        <span>tambos@hotmail.com</span>
      </div>
    </v-toolbar>

    <!-- Navbar principal -->
    <v-toolbar class="px-10" flat color="white" height="80">
      <v-img
        :src="logo"
        alt="Logo Reestructuradora de Tanques"
        max-width="200px"
      />

      <v-spacer />
      <div class="d-none d-md-flex">
        <v-btn href="#inicio" class="text-none" variant="text">Inicio</v-btn>
        <v-btn href="#servicios" class="text-none" variant="text"
          >Servicios</v-btn
        >
        <v-btn href="#nosotros" class="text-none" variant="text"
          >Nosotros</v-btn
        >
        <v-btn
          href="#contacto"
          class="text-none ms-4"
          color="#009684"
          variant="flat"
          rounded
          >Contacto</v-btn
        >
      </div>

      <v-btn icon class="d-md-none" @click="drawer = !drawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-toolbar>

    <v-navigation-drawer v-model="drawer" temporary location="right">
      <v-list>
        <v-list-item href="#inicio" title="Inicio" />
        <v-list-item href="#servicios" title="Servicios" />
        <v-list-item href="#nosotros" title="Nosotros" />
        <v-list-item href="#contacto" title="Contacto" />
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script setup>
import { ref } from "vue";
import logo from "../assets/logo.png";

const drawer = ref(false);
</script>

<style scoped>
.v-toolbar-title span {
  white-space: nowrap;
}
</style>
