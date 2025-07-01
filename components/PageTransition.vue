<template>
  <div ref="transitionEl" class="page-transition">
    <!-- Formes tournantes -->
    <div class="rotating-shape shape-left">
      <img src="/assets/img/cercle.svg" alt="cercle" />
    </div>
    <div class="rotating-shape shape-right">
      <img src="/assets/img/cercle.svg" alt="étoile" />
    </div>
    <div class="rotating-shape shape-top">
      <img src="/assets/img/etoile.svg" alt="cercle" />
    </div>
    <div class="rotating-shape shape-bottom">
      <img src="/assets/img/etoile.svg" alt="étoile" />
    </div>

    <!-- Texte central -->
    <div class="transition-content">
      <h1 class="name">JULIEN HENRY</h1>
      <p class="subtitle">Étudiant développeur web</p>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useRouter } from 'vue-router'

const transitionEl = ref(null)
const router = useRouter()

onMounted(() => {
  router.beforeEach((to, from, next) => {
    transitionEl.value.classList.add('enter')
    setTimeout(() => next(), 600)
  })

  router.afterEach(() => {
    setTimeout(() => {
      transitionEl.value.classList.remove('enter')
    }, 300)
  })
})
</script>

<style scoped>
.page-transition {
  position: fixed;
  inset: 0;
  background: #13462e;
  top: 100%;
  transition: top 0.6s ease-in-out;
  z-index: 9999;
  pointer-events: none;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.page-transition.enter {
  top: 0;
}

/* Texte */
.transition-content {
  z-index: 2;
  text-align: center;
  color: #f3f8f3;
  opacity: 0;
  animation: fadeIn 0.4s ease-out 0.2s forwards;
}

.name {
  font-family: 'Inria Serif', serif;
  font-size: 2.6rem;
  margin-bottom: 0.4rem;
}

.subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.15rem;
  opacity: 0.85;
}

/* Formes */
.rotating-shape {
  position: absolute;
  z-index: 1;
  opacity: 0.3;
}

.rotating-shape img {
  width: 120px;
  animation: rotate 25s linear infinite;
  filter: brightness(0) invert(1); /* rend le SVG blanc si noir */
}

/* Positionnement */
.shape-left {
  left: 15%;
  top: 30%;
}
.shape-right {
  right: 15%;
  bottom: 25%;
}
.shape-top {
  top: 15%;
  left: 45%;
}
.shape-bottom {
  bottom: 10%;
  right: 45%;
}

@keyframes rotate {
  to {
    transform: rotate(360deg);
  }
}

@keyframes fadeIn {
  to {
    opacity: 1;
  }
}

/* Responsive */
@media (max-width: 600px) {
  .name {
    font-size: 2rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .rotating-shape img {
    width: 70px;
  }

  .shape-left {
    left: 10%;
    top: 25%;
  }

  .shape-right {
    right: 10%;
    bottom: 20%;
  }

  .shape-top {
    top: 10%;
    left: 40%;
  }

  .shape-bottom {
    bottom: 8%;
    right: 40%;
  }
}
</style>
