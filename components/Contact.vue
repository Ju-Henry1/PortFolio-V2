<template>
    <!-- CONTACT -->
    <section class="contact">
        <h2>CONTACT</h2>
        <p class="contact-desc">
            Vous voulez me contacter ? N’attendez plus et contactez moi.
        </p>
        <NuxtLink to="/contact" class="contact-btn">
          Me contacter
        </NuxtLink>
    </section>
</template>

<script>
export default {
    name: 'Contact'
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
/* Section Contact */
.contact {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem 4rem 1rem;
  background: #F4FCEF;
}
.contact h2 {
  font-size: 2.5rem;
  color: #1D6F42;
  margin-bottom: 2rem;
  font-family: 'Inria Serif', serif;
}
.contact-desc {
  text-align: center;
  margin-bottom: 2.5rem;
  font-size: 1.1rem;
  color: #205A39;
}
.contact-btn {
  display: block;
  margin: 0 auto;
  background: #1D6F42;
  color: #fff;
  border: none;
  border-radius: 9px;
  padding: 1rem 3rem;
  font-size: 1.1rem;
  font-family: inherit;
  cursor: pointer;
  text-decoration: none;
  transition: background 0.18s;
  text-align: center;
  width: fit-content;
}
.contact-btn:hover {
  background: #22543a;
}
</style>