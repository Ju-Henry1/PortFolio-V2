<template>
  <header class="navbar">
    <NuxtLink to="/" class="logo">JULIEN.<span>H</span></NuxtLink>

    <nav class="nav-links">
      <NuxtLink to="/projets" class="nav-item" :class="{ active: route.path === '/projets' }">
        PROJECTS
      </NuxtLink>

      <div class="separator"></div>

      <NuxtLink to="/contact" class="nav-item" :class="{ active: route.path === '/contact' }">
        CONTACT
      </NuxtLink>
    </nav>
  </header>
</template>

<script setup>
import { useRoute } from 'vue-router'
const route = useRoute()
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inria+Serif:wght@700&family=Inter:wght@700&display=swap');

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  background-color: #f4fcef;
  border-bottom: 1px solid #ccc;
  position: relative;
  z-index: 2;
}

.logo {
  font-size: 2rem;
  font-weight: bold;
  color: #2c714c;
  text-decoration: none;
  font-family: 'Inria Serif', serif;
}

.logo span {
  color: #2c714c;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size: 1rem;
  font-family: 'Inria Serif', serif;
}

.nav-item {
  text-decoration: none;
  color: #2c714c;
  font-weight: bold;
  position: relative;
}

.nav-item.active::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #2c714c;
}

.separator {
  width: 1px;
  height: 1rem;
  background-color: #2c714c;
}
</style>
