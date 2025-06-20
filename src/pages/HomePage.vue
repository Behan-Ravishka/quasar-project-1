<template>
  <q-page class="q-pa-md flex flex-center bg-grey-1">
    <div class="q-pa-xl q-mt-xl text-center" style="max-width: 600px; width: 100%">
      <div class="text-h2 text-primary q-mb-xl">Welcome!</div>
      <div class="text-subtitle1 q-mb-lg">
        This is the home page of your awesome Quasar app. Explore our sections below!
      </div>

      <div class="row justify-center q-gutter-sm">
        <q-btn color="primary" label="About Us" icon="info" unelevated @click="goTo('/about')" />

        <q-btn
          color="secondary"
          label="Contact"
          icon="email"
          unelevated
          @click="goTo('/contact')"
        />
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

function goTo(path) {
  router.push(path)
}
</script>

<style scoped>
.q-page {
  min-height: 100vh;
}
</style>
