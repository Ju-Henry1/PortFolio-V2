<template>
  <section class="hero">
    <!-- Forme gauche -->
    <div class="rotating-shape shape-left">
      <img src="/assets/img/cercle.svg" alt="forme cercle" />
    </div>

    <!-- Texte principal -->
    <div class="content">
      <h1>JULIEN HENRY</h1>
      <p>
        Étudiant en Développement Web,<br />
        à la recherche d'une alternance sur Caen ou Rouen.
      </p>
    </div>

    <!-- Forme droite -->
    <div class="rotating-shape shape-right">
      <img src="/assets/img/etoile.svg" alt="forme étoile" />
    </div>
  </section>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { ref, onMounted } from 'vue'

const route = useRoute()
const currentPath = ref('')

onMounted(() => {
  currentPath.value = route.path
})
</script>

<style scoped>
.hero {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 200px);
  padding: 6rem 2rem;
  background-color: #f3f8f3;
  overflow: hidden;
  text-align: center;
}

.content {
  z-index: 1;
  max-width: 800px;
  padding: 1rem;
}

.content h1 {
  font-size: 3.5rem;
  color: #1c5c3d;
  font-weight: 700;
  margin-bottom: 1rem;
}

.content p {
  font-size: 1.5rem;
  color: #1c5c3d;
  line-height: 1.6;
}

/* Formes tournantes */
.rotating-shape {
  position: absolute;
  z-index: 0;
  opacity: 0.85;
}

.rotating-shape img {
  width: 120px;
  height: auto;
  animation: rotate 25s linear infinite;
}

.shape-left {
  left: -40px;
  top: 20%;
}

.shape-right {
  right: -30px;
  bottom: 15%;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/* Responsive */
@media (max-width: 768px) {
  .hero {
    padding: 5rem 1.5rem;
  }

  .content h1 {
    font-size: 2.4rem;
  }

  .content p {
    font-size: 1.2rem;
  }

  .rotating-shape img {
    width: 80px;
  }

  .shape-left {
    left: -30px;
    top: 10%;
  }

  .shape-right {
    right: -20px;
    bottom: 10%;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: 4rem 1rem;
  }

  .content h1 {
    font-size: 2rem;
  }

  .content p {
    font-size: 1rem;
  }

  .rotating-shape img {
    width: 60px;
  }
}
</style>
