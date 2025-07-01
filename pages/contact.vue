<template>
  <Header />

  <section class="contact-page">
    <div class="container">
      <h1>Me contacter</h1>
      <p class="intro">
        Tu as une question, un projet ou tu veux simplement discuter ?<br />
        Voici les meilleurs moyens de me joindre :
      </p>

      <div class="contact-grid">
        <!-- E-mail -->
        <a href="mailto:julien.henry@email.com" class="contact-item">
          <span class="icon">📧</span>
          <div>
            <h3>E-mail</h3>
            <p>henry.juliennn@email.com</p>
          </div>
        </a>

        <!-- LinkedIn -->
        <a
          href="https://www.linkedin.com/in/julien-henry76"
          class="contact-item"
          target="_blank"
        >
          <span class="icon">🔗</span>
          <div>
            <h3>LinkedIn</h3>
            <p>linkedin.com/in/julien-henry76</p>
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
  </section>

  <Footer />
</template>

<style scoped>
.contact-page {
  background:#f5faf5;
  padding:5rem 2rem;
  font-family:'Inter',sans-serif;
}

.container {
  max-width:800px;
  margin:auto;
  text-align:center;
}

h1{
  font-size:2.4rem;
  color:#2c714c;
  margin-bottom:1.2rem;
}

.intro{
  font-size:1.05rem;
  color:#2c4f3e;
  margin-bottom:2.5rem;
  line-height:1.6;
}

/* --- GRILLE FLUIDE --- */
.contact-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
  gap:1.5rem;
  justify-items:center;     /* centre les cartes */
}

.contact-item{
  background:#fff;
  border:1px solid #e0e7e0;
  border-radius:12px;
  padding:1.4rem 1.6rem;
  width:100%;               /* occupe toute la cellule */
  max-width:320px;
  display:flex;
  gap:1rem;
  text-align:left;
  text-decoration:none;
  transition:background .25s;
  box-sizing:border-box;
}

.contact-item:hover{
  background:#e8f5e8;
  border-color:#c1e0c1;
}

.icon{
  font-size:1.8rem;
  color:#0b3320;
  flex-shrink:0;
}

.contact-item h3{
  font-size:1.05rem;
  margin:0;
  color:#0b3320;
}

.contact-item p{
  font-size:.95rem;
  color:#40614f;
  margin-top:.3rem;
  word-break:break-word;    /* évite le débordement */
}

/* --- PETITS ÉCRANS --- */
@media(max-width:400px){
  h1{font-size:2rem;}
  .intro{font-size:.95rem;}
  .contact-item{
    padding:1.2rem 1.2rem;
  }
}
</style>
