<template>

  <Header />

  <section class="contact-page">
    <div class="container">
      <h1>Me contacter</h1>
      <p class="intro">
        Tu as une question, un projet ou tu veux simplement discuter ?
        <br />
        Voici les meilleurs moyens de me joindre :
      </p>

      <div class="contact-grid">
        <!-- E-mail -->
        <a href="mailto:julien.henry@email.com" class="contact-item">
          <span class="icon">📧</span>
          <div>
            <h3>E‑mail</h3>
            <p>henry.juliennn@email.com</p>
          </div>
        </a>

        <!-- LinkedIn -->
        <a
          href="www.linkedin.com/in/julien-henry76"
          class="contact-item"
          target="_blank"
        >
          <span class="icon">🔗</span>
          <div>
            <h3>LinkedIn</h3>
            <p>www.linkedin.com/in/julien-henry76</p>
          </div>
        </a>

        <!-- Téléphone -->
        <a href="tel:+33630897219" class="contact-item">
          <span class="icon">📞</span>
          <div>
            <h3>Téléphone</h3>
            <p>+33 6 30 89 72 19</p>
          </div>
        </a>
      </div>
    </div>
    <br>
  </section>

  <Footer />

</template>

<script setup>
// Aucune logique JS nécessaire ici
</script>

<style scoped>
.contact-page {
  background-color: #f5faf5;
  padding: 5rem 2rem;
  font-family: 'Inter', sans-serif;
}

.container {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 2.8rem;
  color: #2c714c;
  margin-bottom: 1.2rem;
}

.intro {
  font-size: 1.1rem;
  color: #2c4f3e;
  margin-bottom: 3rem;
  line-height: 1.6;
}

.contact-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
}

.contact-item {
  background: white;
  border: 1px solid #e0e7e0;
  border-radius: 12px;
  padding: 1.5rem 2rem;
  width: 260px;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  text-align: left;
  text-decoration: none;
  transition: all 0.3s ease;
}

.contact-item:hover {
  background-color: #e8f5e8;
  border-color: #c1e0c1;
}

.icon {
  font-size: 1.8rem;
  color: #0b3320;
  flex-shrink: 0;
}

.contact-item h3 {
  font-size: 1.1rem;
  margin: 0;
  color: #0b3320;
}

.contact-item p {
  font-size: 0.95rem;
  color: #40614f;
  margin-top: 0.3rem;
}

/* Responsive */
@media (max-width: 600px) {
  .contact-grid {
    flex-direction: column;
    align-items: center;
  }

  .contact-item {
    width: 100%;
    max-width: 320px;
  }
}
</style>
