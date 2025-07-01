<template>
    <section class="infos">
        <h2>EN SAVOIR +</h2>
        <p class="infos-desc">
            Pour en savoir plus sur moi, n’hésitez pas à visiter mes profils ou télécharger mon CV !
        </p>
        <br>
        <br>
        <div class="infos-cards">
            <!-- Carte GitHub -->
            <div class="infos-card">
                <div class="infos-icon">
                    <img src="/assets/img/savoir-plus/github.svg" alt="GitHub"/>
                </div>
                <p>
                    Retrouvez l’ensemble de mes projets<br> <b>open source</b><br>
                    et contributions sur mon profil <b>GitHub</b>.
                </p>
                <a href="https://github.com/Ju-Henry1" target="_blank" class="infos-btn">
                    <img src="/assets/img/savoir-plus/fleche.svg" alt="" class="arrow-icon"/>
                    Voir
                </a>
            </div>
            <!-- Carte CV -->
            <div class="infos-card">
                <div class="infos-icon">
                    <img src="/assets/img/savoir-plus/cv.svg" alt="CV"/>
                </div>
                <p>
                    Besoin de plus d’infos ?<br>
                    <b>Téléchargez</b> mon CV<br>
                    pour découvrir mon parcours complet.
                </p>
                <a href="/CV_JULIEN_HENRY.pdf" target="_blank" class="infos-btn">
                    <img src="/assets/img/savoir-plus/fleche.svg" alt="" class="arrow-icon"/>
                    Télécharger
                </a>
            </div>
            <!-- Carte LinkedIn -->
            <div class="infos-card">
                <div class="infos-icon">
                    <img src="/assets/img/savoir-plus/linkedln.svg" alt="LinkedIn"/>
                </div>
                <p>
                    Envie de se connecter ou <b>d’échanger</b> ?<br>
                    Rendez-vous sur mon LinkedIn,<br>
                    <b>Rejoignez-moi</b> pour rester en contact.
                </p>
                <a href="https://linkedin.com/in/julien-henry76" target="_blank" class="infos-btn">
                    <img src="/assets/img/savoir-plus/fleche.svg" alt="" class="arrow-icon"/>
                    Voir
                </a>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'EnSavoirPlus'
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
/* Savoir plus */ 

.infos {
  max-width: 1200px;
  margin: 4rem auto 0 auto;
  padding: 2rem 1rem 0 1rem;
  background: #F4FCEF;
}
.infos h2 {
  font-size: 2.5rem;
  color: #1D6F42;
  margin-bottom: 1.5rem;
  font-family: 'Inria Serif', serif;
}
.infos-desc {
  text-align: center;
  color: #205A39;
  margin-bottom: 2rem;
  font-size: 1.1rem;
  font-family: 'Inter', sans-serif;
}
.infos-cards {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-bottom: 4rem;
  flex-wrap: wrap;
}
.infos-card {
  background: none;
  border: 1px solid #1D6F42;
  border-radius: 8px;
  width: 320px;
  min-width: 260px;
  text-align: center;
  padding: 2.5rem 1rem 1.5rem 1rem;
  position: relative;
  transition: box-shadow 0.2s;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}
.infos-card:hover {
  box-shadow: 0 8px 30px rgba(44,113,76,0.08);
  background: rgba(44,113,76,0.02);
}
.infos-icon {
  position: absolute;
  top: -28px;
  left: 50%;
  transform: translateX(-50%);
  background: #2c714c;
  border-radius: 7px;
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #E3E5BC;
}
.infos-icon img {
  height: 32px;
  width: 32px;
  display: block;
}
.infos-card p {
  margin-top: 24px;
  color: #205A39;
  font-size: 1rem;
  font-family: 'Inter', sans-serif;
}
.infos-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4em;
  background: #1D6F42;
  color: #E3E5BC;
  border: none;
  border-radius: 7px;
  padding: 0.7em 2.3em;
  font-size: 1rem;
  margin-top: 1rem;
  font-family: inherit;
  cursor: pointer;
  text-decoration: none;
  transition: background 0.18s;
}
.infos-btn:hover {
  background: #22543a;
}

.arrow-icon {
  width: 16px;
  height: 16px;
  fill: #E3E5BC;
  transition: transform 0.2s;
}

/* Responsive */
@media (max-width: 950px) {
  .infos-cards { flex-direction: column; gap: 3rem; align-items: center; }
  .infos-card { width: 90%; min-width: 180px; }
}
</style>