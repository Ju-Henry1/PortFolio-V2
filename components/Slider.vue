<template>
<section class="skills">
        <div class="skills-inner">
            <h2>COMPETENCE</h2>
            <div class="skills-box">
                <div class="skills-slider">
                    <img src="/assets/img/slider/figma.svg" alt="Figma" />
                    <img src="/assets/img/slider/github.svg" alt="Github" />
                    <img src="/assets/img/slider/gitlab.svg" alt="gitlab" />
                    <img src="/assets/img/slider/html-css.png" alt="html-css" />
                    <img src="/assets/img/slider/javascript.svg" alt="Javascript" />
                    <img src="/assets/img/slider/nuxt-js.svg" alt="Nuxt" />
                    <img src="/assets/img/slider/vue-js.svg" alt="Vue Js" />
                    <img src="/assets/img/slider/php.png" alt="Php" />
                    <img src="/assets/img/slider/Symfony.png" alt="Symfony" />
                    <img src="/assets/img/slider/wordpress.svg" alt="Wordpress" />
                    <img src="/assets/img/slider/sql.png" alt="Sql" />
                    <img src="/assets/img/slider/python.svg" alt="Python" />
                    <img src="/assets/img/slider/Flutter_logo.png" alt="Flutter" />
                    <img src="/assets/img/slider/Postman.png" alt="Postaman" />
                    <!-- DUPLICATA -->
                    <img src="/assets/img/slider/figma.svg" alt="Figma" />
                    <img src="/assets/img/slider/github.svg" alt="Github" />
                    <img src="/assets/img/slider/gitlab.svg" alt="gitlab" />
                    <img src="/assets/img/slider/html-css.png" alt="html-css" />
                    <img src="/assets/img/slider/javascript.svg" alt="Javascript" />
                    <img src="/assets/img/slider/nuxt-js.svg" alt="Nuxt" />
                    <img src="/assets/img/slider/vue-js.svg" alt="Vue Js" />
                    <img src="/assets/img/slider/php.png" alt="Php" />
                    <img src="/assets/img/slider/Symfony.png" alt="Symfony" />
                    <img src="/assets/img/slider/wordpress.svg" alt="Wordpress" />
                    <img src="/assets/img/slider/sql.png" alt="Sql" />
                    <img src="/assets/img/slider/python.svg" alt="Python" />
                    <img src="/assets/img/slider/Flutter_logo.png" alt="Flutter" />
                    <img src="/assets/img/slider/Postman.png" alt="Postaman" />
                </div>
            </div>
        </div>
    </section>
</template>

<script>

export default {
    name: 'Slider'
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
/* slider */
/* ----------- SKILLS ----------- */
.skills {
  background-color: #1f6840;
  width: 100%;
  padding: 3rem 0;  /* padding vertical uniquement */
  color: #f0f7e5;
  font-family: 'Inria Serif', serif;
  margin-top: 60px;
}

/* Le wrapper qui centre et limite le contenu */
.skills-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;  /* padding horizontal, identique à .projects */
}

.skills h2 {
  font-size: 2rem;
  font-weight: 700;
  color: #f0f7e5;
  margin-bottom: 2rem;
}

.skills-box {
  border: 1px solid #f0f7e5;
  padding: 3rem;
  overflow: hidden;
  position: relative;
}

.skills-slider {
  display: flex;
  gap: 3rem;
  animation: scrollSkills 24s linear infinite;
  /* Attention : pas de wrap, pas de largeur max */
  width: max-content;
}

.skills-slider img {
  height: 60px;
  width: auto;
  flex-shrink: 0;
  filter: brightness(95%) contrast(110%);
  transition: transform 0.3s ease;
  display: block;
}

.skills-slider img:hover {
  transform: scale(1.1);
}

@keyframes scrollSkills {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
</style>