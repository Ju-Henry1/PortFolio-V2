<template>
    <section class="projects">
        <h2>PROJECTS</h2>

        <NuxtLink to="/projets/julien-dubois" class="project-item">
          <span class="project-index-title">01. CABINET JULIEN DUBOIS</span>
          <span class="project-action">+</span>
        </NuxtLink>

        <NuxtLink to="/projets/doczy" class="project-item">
          <span class="project-index-title">02. DOCZY</span>
          <span class="project-action">+</span>
        </NuxtLink>

        <NuxtLink to="/projets/as-giberville" class="project-item">
          <span class="project-index-title">03. AS GIBERVILLE</span>
          <span class="project-action">+</span>
        </NuxtLink>

        <NuxtLink to="/projets" class="project-item">
          <span class="project-index-title">XX. MORE PROJECT</span>
          <span class="project-action">+</span>
        </NuxtLink>
    </section>
</template>

<script>
export default {
    name: 'Project-index'
}

import { useRoute } from 'vue-router'
import { ref, onMounted } from 'vue'
const route = useRoute()
const currentPath = ref('')
onMounted(() => {
    currentPath.value = route.path
})


</script>

<style scoped>
/* Projets */ 
.projects {
  background-color: #F4FCEF;
  padding: 1.5rem 1rem;
  max-width: 1200px;
  margin: 0 auto;
}

.project-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-top: 1px solid #2c714c;
  padding: 1.5rem 0;
  text-decoration: none;
  color: inherit;
  position: relative;
}

.project-item:hover {
  background-color: rgba(44, 113, 76, 0.05);
}

.project-item:last-child {
  border-bottom: 1px solid #2c714c;
}

.project-index-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #1D6F42;
  margin-bottom: 0.5rem;
  text-decoration: none;
  font-family: 'Inria Serif', serif;
  transition: color 0.2s ease;
}

.project-action {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-right: 1rem;
  color: #1D6F42;
  text-decoration: none;
  font-size: 1.5rem;
}

.projects h2 {
  font-size: 2.5rem;
  color: #1D6F42;
  margin-bottom: 3rem;
}

</style>