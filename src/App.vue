<script lang="ts" setup>
import { TheImageContainer } from '@/composables/image'
</script>

<template>
  <main font-sans p="x-4 y-10" text="center gray-700 dark:gray-200">
    <router-view />
  </main>
  <TheImageContainer />
  <footer text-center>
    <Footer />
  </footer>
</template>

