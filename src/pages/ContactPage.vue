<template>
  <q-page class="q-pa-md flex flex-center bg-grey-1">
    <q-card class="q-pa-lg" style="max-width: 500px; width: 100%">
      <q-card-section>
        <div class="text-h5 text-primary text-center">Contact Us</div>
      </q-card-section>

      <q-separator />

      <q-card-section class="text-body1">
        <p class="text-center">
          We'd love to hear from you. Reach out to us through any of the methods below.
        </p>

        <div class="q-mt-md">
          <q-item clickable tag="a" href="mailto:contact@example.com" target="_blank">
            <q-item-section avatar>
              <q-icon name="email" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Email</q-item-label>
              <q-item-label caption>contact@example.com</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable tag="a" href="tel:+1234567890">
            <q-item-section avatar>
              <q-icon name="phone" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Phone</q-item-label>
              <q-item-label caption>+1 (234) 567-890</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable tag="a" href="https://instagram.com/yourprofile" target="_blank">
            <q-item-section avatar>
              <q-icon name="mdi-instagram" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Instagram</q-item-label>
              <q-item-label caption>@yourprofile</q-item-label>
            </q-item-section>
          </q-item>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup></script>

<style scoped>
.q-page {
  min-height: 100vh;
}
</style>
