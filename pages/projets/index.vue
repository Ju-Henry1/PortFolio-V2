<template>

  <Header />

  <div class="page-wrapper">
    <!-- bloc slider + pastilles côte à côte -->
    <div class="slider-block">
      <!-- Image & click‑to‑project link -->
      <NuxtLink :to="`/projets/${projects[currentIndex].slug}`" class="slider">
        <transition name="fade" mode="out-in">
          <img
            :src="projects[currentIndex].image"
            :key="projects[currentIndex].image"
            class="slide-image"
            alt="image du projet"
          />
        </transition>
      </NuxtLink>

      <!-- Dots indicator (à droite, hors de l'image) -->
      <ul class="dots">
        <li
          v-for="(p, i) in projects"
          :key="i"
          :class="['dot', { active: i === currentIndex }]"
          @click="goTo(i)"
        ></li>
      </ul>
    </div>

    <!-- Nom du projet sous l'image -->
    <h2 class="project-title">{{ projects[currentIndex].name }}</h2>
  </div>

  <Footer />

</template>

<script setup>

useHead({
  title: 'Projets – Julien Henry',
})

import { ref, onMounted, onBeforeUnmount } from 'vue'
import { useRoute } from 'vue-router'

// Images depuis le dossier `public/img/...` (pas besoin de import)
const projects = [
  {
    name: 'Cabinet Julien Dubois',
    slug: 'julien-dubois',
    image: '/img/projets/cabinet-julien-dubois/cabinet-julien-dubois.png',
    url: '/projets/julien-dubois',
  },
  {
    name: 'Doczy',
    slug: 'doczy',
    image: '/img/projets/doczy/doczy.png',
    url: '/projets/doczy',
  },
  {
    name: 'AS Giberville',
    slug: 'as-giberville',
    image: '/img/projets/as-giberville/as-giberville.png',
    url: '/projets/as-giberville',
  },
  {
    name: 'Breakout',
    slug: 'breakout',
    image: '/img/projets/breakout/breakout.png',
    url: '/projets/breakout',
  },
  {
    name: 'Plateforme Mini-Jeux',
    slug: 'mini-jeux',
    image: '/img/projets/mini-jeux/mini-jeux.png',
    url: '/projets/mini-jeux',
  },
]

const currentIndex = ref(0)
let timer

const next = () => {
  currentIndex.value = (currentIndex.value + 1) % projects.length
}

const restartTimer = () => {
  clearInterval(timer)
  timer = setInterval(next, 10000)
}

const goTo = (index) => {
  currentIndex.value = index
  restartTimer()
}

onMounted(() => {
  timer = setInterval(next, 10000)
})

onBeforeUnmount(() => {
  clearInterval(timer)
})

const route = useRoute()
const currentPath = ref(route.path)
</script>


<style scoped>
/* ==== Global Wrapper ==== */
.page-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 60px;
  padding-bottom: 40px;
  background-color: #f3f8f3;
  min-height: 100vh;
  box-sizing: border-box;
}

/* ==== Bloc contenant image + pastilles ==== */
.slider-block {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px; /* espace entre l’image et les pastilles */
  width: 90%;
  max-width: 860px;
  flex-wrap: wrap; /* pour éviter tout débordement */
}

/* ==== Lien contenant l’image (slider) ==== */
.slider {
  width: 100%;
  max-width: 700px;
  aspect-ratio: 16 / 10;
  overflow: hidden;
  background: #eef8ee;
  border: 1px solid #ccc;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
  display: block;
}

/* ==== Image du projet ==== */
.slide-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  background-color: white;
  display: block;
  max-height: 100%;
}

/* ==== Animation de fondu entre images ==== */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* ==== Liste des pastilles (dots) ==== */
.dots {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

/* ==== Style des pastilles ==== */
.dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  border: 2px solid #0b3320;
  background: #fff;
  cursor: pointer;
  transition: background 0.3s;
}

.dot:hover {
  background: #cfe3cf;
}

.dot.active {
  background: #0b3320;
}

/* ==== Titre sous le slider ==== */
.project-title {
  margin-top: 28px;
  font-size: 26px;
  font-weight: 600;
  color: #0b3320;
  text-align: center;
}

/* ==== Responsive mobile/tablette ==== */
@media (max-width: 768px) {
  /* Les éléments sont empilés verticalement */
  .slider-block {
    flex-direction: column;
    gap: 20px;
  }

  /* Les pastilles passent sous l’image */
  .dots {
    flex-direction: row;
    justify-content: center;
    gap: 14px;
  }
}

</style>
