<script setup>
import PageTransition from '~/components/PageTransition.vue'
import { Analytics } from '@vercel/analytics/nuxt';
</script>


<template>
  <Analytics />
  <PageTransition />
  <NuxtPage />
</template>

