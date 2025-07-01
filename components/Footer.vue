<template>
  <footer class="footer">
    <div class="container">
      <!-- Colonne gauche -->
      <div class="footer-left">
        <p>© {{ year }} Julien Henry</p>
      </div>

      <!-- Réseaux sociaux avec icônes SVG perso -->
      <div class="footer-social">
        <a href="mailto:henry.juliennn@email.com" aria-label="Mail">
          <img src="/icons/mail.svg" alt="Mail" class="icon" />
        </a>
        <a href="https://linkedin.com/in/julien-henry76" target="_blank" aria-label="LinkedIn">
          <img src="/icons/linkedin.svg" alt="LinkedIn" class="icon" />
        </a>
        <a href="https://github.com/Ju-Henry1" aria-label="Github">
          <img src="/icons/github.svg" alt="Github" class="icon" />
        </a>
        <a href="tel:+33630897219" aria-label="Téléphone">
          <img src="/icons/phone.svg" alt="Téléphone" class="icon" />
        </a>
      </div>

      <!-- Liens -->
      <nav class="footer-links">
        <NuxtLink to="/">Accueil</NuxtLink>
        <NuxtLink to="/projets">Projets</NuxtLink>
        <NuxtLink to="/contact">Contact</NuxtLink>
      </nav>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  background-color: #13462e;
  color: #f3f8f3;
  padding: 1.8rem 1rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  gap: 1.5rem;
  flex-wrap: wrap;
  align-items: center;
}

.footer-left {
  flex: 1;
}

.footer-social {
  flex: 1;
  display: flex;
  justify-content: center;
  gap: 1.2rem;
}

.icon {
  width: 30px;
  height: 30px;
  filter: brightness(0) invert(1); /* rend le SVG blanc */
  transition: opacity 0.3s ease;
}
.footer-social a:hover .icon {
  opacity: 0.7;
}

.footer-links {
  flex: 1;
  display: flex;
  justify-content: flex-end;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-links a {
  color: #f3f8f3;
  text-decoration: none;
  transition: opacity 0.3s ease;
}
.footer-links a:hover {
  opacity: 0.75;
}

/* Responsive */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .footer-links {
    justify-content: center;
  }

  .footer-left {
    order: 3;
    margin-top: 1rem;
  }
}
</style>
