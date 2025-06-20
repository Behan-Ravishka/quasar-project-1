<template>
  <q-page class="q-pa-md flex flex-center column items-center text-center">
    <q-avatar size="100px" class="q-mb-md">
      <img src="https://cdn.quasar.dev/logo-v2/svg/logo.svg" alt="Logo" />
    </q-avatar>

    <div class="text-h5 text-primary q-mb-sm">About This App</div>

    <div class="text-subtitle1 q-mb-md">
      This is a simple Quasar Framework application built with Vue 3.
    </div>

    <q-separator spaced />

    <q-card flat bordered class="q-pa-md q-mt-md" style="max-width: 400px">
      <q-card-section>
        <div class="text-subtitle2 text-weight-bold">Built With</div>
        <q-list dense>
          <q-item>
            <q-item-section>Vue 3</q-item-section>
          </q-item>
          <q-item>
            <q-item-section>Quasar Framework</q-item-section>
          </q-item>
          <q-item>
            <q-item-section>ESLint + Prettier</q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  name: 'AboutPage',
}
</script>

<style scoped></style>
