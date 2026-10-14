# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- `npm run dev` — start the Vite dev server with HMR
- `npm run build` — production build to `dist/`
- `npm run preview` — serve the built `dist/` locally

There is no test runner, linter, or formatter configured.

## Architecture

Single-page marketing/landing site for **Reconstructora de Tambos**, a Hermosillo (Sonora, Mexico) company that reconditions industrial drums/tanks (tambos) and handles waste collection. The UI copy is in Spanish.

Stack: **Vue 3** (`<script setup>` SFCs) + **Vuetify 3** + Vite. Sass is available for styling, though components mostly use scoped plain CSS.

- `src/main.js` registers Vuetify globally (all components and directives via `vuetify/components` + `vuetify/directives`) and mounts the app. Any new Vuetify component or custom plugin wiring goes here.
- `src/App.vue` composes the entire page as a fixed vertical sequence of section components inside `<v-app>` / `<v-main>`: `Navbar`, `HeroSection`, `ServiceSection`, `About`, `ContactSection`, `FooterSection`. The page is one scroll; there is no router.
- Navigation is anchor-based. Each section `<section>` carries an `id` (`#inicio`, `#servicios`, `#nosotros`, `#contacto`) and the `Navbar` links jump to those ids. Keep section ids in sync with the Navbar `href`s when renaming or adding sections.
- `HelloWorld.vue` is leftover scaffolding and is not mounted.

### Contact form (`src/components/ContactSection.vue`)

Submissions are sent client-side via **EmailJS** (`@emailjs/browser`), not a backend. The EmailJS service/template/public-key IDs are inlined in `handleSubmit`. Success/error feedback uses **SweetAlert2** (`Swal`); the phone field is masked with **vue-the-mask** (`v-mask`). Responsive behavior reads Vuetify's `useDisplay()` breakpoints.

### Conventions

- Static assets (images, the `.mp4` video) live in `src/assets/` and are imported into components; `public/` holds only the favicon.
- Brand green is used inline across components (notably `#009875` / `#00996c` / `#009684`) rather than a central theme token.
