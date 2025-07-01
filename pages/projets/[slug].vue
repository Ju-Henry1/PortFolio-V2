<template>
  <Header />

  <div v-if="project" class="project-detail">
    <div class="left-panel" id="contenu">
      <h1 class="title">{{ project.title }}</h1>
      <p class="subtitle subtitle-tight">{{ project.subtitle }}</p>

      <div class="bloc">
        <p class="paragraph" v-html="project.context"></p>
        <p class="paragraph" v-html="project.solution"></p>
      </div>

      <div class="bloc">
        <h3 class="subheading">Outils & technologies</h3>
        <ul class="tech-list">
          <li v-for="t in project.tools" :key="t">{{ t }}</li>
        </ul>
      </div>

      <a
        v-if="project.siteUrl"
        :href="project.siteUrl"
        target="_blank"
        rel="noopener noreferrer"
        class="see-site"
      >↗ Voir le site</a>
    </div>

    <div class="right-panel" id="contenu">
      <div class="image-scroll">
        <img
          v-for="(img, i) in project.images"
          :key="i"
          :src="img"
          :alt="`${project.title} - visuel ${i + 1}`"
          class="project-image"
        />
      </div>
    </div>
  </div>

  <div v-else class="not-found">
    <h2>Projet non trouvé 😕</h2>
    <NuxtLink to="/">← Retour à l’accueil</NuxtLink>
  </div>
  <Footer />
</template>

<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const projects = [
  {
    slug: 'julien-dubois',
    title: 'Cabinet Julien Dubois',
    subtitle: 'Refonte de site vitrine pour un cabinet de géomètre basé à Deauville',
    context: `<strong>Cabinet Julien Dubois</strong> m’a confié la refonte complète de leur site vitrine. L’objectif était de proposer une nouvelle interface reflétant leur expertise en géométrie tout en respectant la charte graphique issue de leur logo.`,
    solution: `J’ai conçu une maquette sur <strong>Figma</strong>, puis développé le site en <strong>HTML</strong>, <strong>CSS</strong> et <strong>JavaScript</strong>. Le site est <em>responsive</em> et hébergé sur <strong>OVH</strong>.`,
    tools: ['Figma', 'HTML', 'CSS', 'JavaScript'],
    images: [
      '/img/projets/cabinet-julien-dubois/maquette.png',
      '/img/projets/cabinet-julien-dubois/cabinet-julien-dubois.png',
      '/img/projets/cabinet-julien-dubois/page-prestations.png',
      '/img/projets/cabinet-julien-dubois/page-contact.png'
    ],
    siteUrl: 'https://cabinetjuliendubois.fr'
  },
  {
    slug: 'doczy',
    title: 'Doczy',
    subtitle: 'Création d\'une plateforme web de génération de documents',
    context: `<strong>Doczy</strong> est née d’un besoin de simplifier la création de documents pour les indépendants et petites entreprises.`,
    solution: `Développée avec <strong>Nuxt.js</strong>, l’application permet la création de <em>PDF</em> instantanés sans stockage distant. Le tout est géré 100% en local dans le navigateur.`,
    tools: ['Nuxt', 'Vue.js', 'Css'],
    images: [
      '/img/projets/doczy/doczy.png',
      '/img/projets/doczy/doczy-2.png',
      '/img/projets/doczy/doczy-3.png',
      '/img/projets/doczy/doczy-4.png',
      '/img/projets/doczy/doczy-5.png',
      '/img/projets/doczy/doczy-6.png',
      '/img/projets/doczy/doczy-7.png',
      '/img/projets/doczy/doczy-8.png',

    ]
  },
  {
    slug: 'as-giberville',
    title: 'AS Giberville',
    subtitle: 'Création d’un site web pour un club sportif lors d’un projet d’équipe',
    context: `Dans le cadre d’un projet académiques, nous avons travaillé en équipe de 4 (2 designers, 1 marketing, 1 développeur) pour accompagner le club de basket <strong>AS Giberville</strong> situées à coté de <strong>Caen</strong> dans la refonte de leur communication digitale.`,
    solution: `J’ai pris en charge toute la partie développement du site avec <strong>Nuxt.js</strong>. Nous avons également intégré un <strong>CMS Directus</strong> pour permettre aux membres du club de gérer eux-mêmes leur contenu sans compétences techniques et ainsi rajouter des actualités, des événements, etc.`,
    tools: ['Nuxt', 'Vue.js', 'Directus', 'Figma'],
    images: [
      '/img/projets/as-giberville/as-giberville.png',
      '/img/projets/as-giberville/as-giberville-2.png',
      '/img/projets/as-giberville/as-giberville-3.png',
      '/img/projets/as-giberville/as-giberville-4.png',
      '/img/projets/as-giberville/as-giberville-5.png',
      '/img/projets/as-giberville/as-giberville-6.png',
      '/img/projets/as-giberville/as-giberville-7.png',
      '/img/projets/as-giberville/as-giberville-8.png',
      '/img/projets/as-giberville/as-giberville-9.png',
      '/img/projets/as-giberville/as-giberville-10.png'
    ]
  },
  {
    slug: 'breakout',
    title: 'Breakout',
    subtitle: 'Création d’un jeu de type Breakout en début de 3e année de Bachelor',
    context: `Ce projet a été réalisé en début de 3e année dans le cadre d’un travail de groupe. Par équipe de 3, nous devions développer un jeu inspiré du célèbre <em>Breakout</em>, en mettant l’accent sur la logique de jeu, la gestion des collisions et la dynamique du score.`,
    solution: `J’ai participé à la conception du gameplay en <strong>Vue.js</strong> avec une intégration sous <strong>Nuxt</strong>. Le projet nous a permis de consolider notre compréhension du DOM, des canvas HTML5, ainsi que de la structure modulaire d’une application Nuxt.`,
    tools: ['Nuxt', 'Vue.js', 'TypeScript'],
    images: [
      '/img/projets/breakout/breakout.png',

    ]
  },
  {
    slug: 'mini-jeux',
    title: 'Plateforme Jeux',
    subtitle: 'Plateforme de jeux incluant des mini-jeux et des jeux de soirée',
    context: `Ce projet personnel a été réalisé dans le but de centraliser plusieurs petits jeux web simples et accessibles, à destination d’un public varié. On y retrouve à la fois des mini-jeux classiques et des jeux conviviaux pensés pour les soirées.`,
    solution: `J’ai développé la plateforme en <strong>HTML</strong>, <strong>CSS</strong> et <strong>JavaScript</strong>, avec une interface intuitive et une navigation fluide entre les jeux. Le projet m’a permis d’explorer différentes mécaniques de jeu et d’optimiser le code pour une bonne réactivité.`,
    tools: ['HTML', 'CSS', 'JavaScript'],
    images: [
      '/img/projets/mini-jeux/mini-jeux.png',
      '/img/projets/mini-jeux/mini-jeux-2.png',
      '/img/projets/mini-jeux/mini-jeux-3.png',
      '/img/projets/mini-jeux/mini-jeux-4.png',
      '/img/projets/mini-jeux/mini-jeux-5.png',
      '/img/projets/mini-jeux/mini-jeux-6.png'
    ]
  }
]

const route = useRoute()
const project = computed(() =>
  projects.find(p => p.slug === route.params.slug)
)
</script>

<style scoped>
.project-detail {
  display: flex;
  background: #edf7ed;
  min-height: 100vh;
  flex-direction: row;
  flex-wrap: nowrap;
}

/* === Colonne gauche : texte === */
.left-panel {
  flex: 0 0 50%;
  padding: 3rem;
  position: sticky;
  top: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  font-family: 'Inter', sans-serif;
  color: #0D4D2A;
  box-sizing: border-box;
}

/* === Colonne droite : images === */
.right-panel {
  flex: 1;
  overflow-y: auto;
  padding: 3rem;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

/* === Titres et paragraphes === */
.title {
  font-size: 24px;
  font-weight: 800;
  color: #0b3320;
  margin-bottom: 0.1rem;
}

.subtitle {
  font-size: 14px;
  color: #8ca494;
  margin-bottom: 1.2rem;
}

.bloc {
  margin-bottom: 1rem;
}

.paragraph {
  font-size: 16px;
  line-height: 1.5;
  color: #0D4D2A;
}

.subheading {
  font-size: 16px;
  font-weight: 600;
  color: #0D4D2A;
  margin-bottom: 0.3rem;
}

/* === Liste des outils === */
.tech-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  list-style: none;
  padding: 0;
  margin: 0;
}

.tech-list li {
  background: #f5f5f5;
  padding: 6px 12px;
  border-radius: 8px;
  font-size: 13px;
  color: #0b3320;
  border: 1px solid #ccc;
}

/* === Lien vers le site === */
.see-site {
  display: inline-block;
  margin-top: 1.5rem;
  background: #0b3320;
  color: white;
  padding: 10px 18px;
  border-radius: 10px;
  font-size: 14px;
  text-decoration: none;
  transition: background 0.3s;
}
.see-site:hover {
  background: #145a36;
}

/* === Images === */
.image-scroll {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.project-image {
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  object-fit: contain;
}

/* === Fallback si projet introuvable === */
.not-found {
  padding: 4rem;
  text-align: center;
}

/* === RESPONSIVE === */
@media (max-width: 900px) {
  .project-detail {
    flex-direction: column;
  }

  .left-panel {
    position: relative;
    width: 100%;
    height: auto;
    padding: 2rem 1.5rem;
  }

  .right-panel {
    width: 100%;
    padding: 2rem 1.5rem;
  }

  .project-image {
    max-width: 100%;
  }
}

</style>
