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
/* Page wrapper */
.page-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 60px;
  padding-bottom: 40px;
  background-color: #f3f8f3;
  min-height: 100vh;
}

/* Slider + dots ensemble */
.slider-block {
  display: flex;
  align-items: center;
  gap: 24px; /* espace entre image et dots */
  width: 90%;
  max-width: 860px;
}

/* Slider (image) */
.slider {
  position: relative;
  flex: 1 1 0;
  aspect-ratio: 16 / 10;
  overflow: hidden;
  background: #eef8ee;
  border: 1px solid #ccc;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
  display: block;
}

.slide-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  background-color: white;
}

/* Fade animation */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Dots */
.dots {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  border: 2px solid #0b3320;
  background: #ffffff;
  cursor: pointer;
  transition: background 0.3s;
}
.dot:hover {
  background: #cfe3cf;
}
.dot.active {
  background: #0b3320;
}

/* Titre du projet */
.project-title {
  margin-top: 28px;
  font-size: 26px;
  font-weight: 600;
  color: #0b3320;
  text-align: center;
}

/* Responsive : dots en bas pour très petits écrans */
@media (max-width: 640px) {
  .slider-block {
    flex-direction: column;
  }
  .dots {
    flex-direction: row;
    gap: 16px;
  }
}
</style>
