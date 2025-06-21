<template>
  <q-page class="contact-page flex flex-center q-pa-md">
    <div class="contact-container bg-grey-10 q-pa-lg rounded-borders shadow-2">
      <div class="row q-col-gutter-xl items-stretch">
        <!-- Left Column: Contact Information -->
        <div class="col-12 col-md-5">
          <div class="text-overline text-grey-5">Get in touch</div>
          <h2 class="text-h4 text-weight-bold q-my-sm text-white">Contact Me</h2>
          <p class="text-body1 text-grey-4 q-mb-lg">
            I'm open to collaborations, freelance work, and job opportunities. If you have a
            question or just want to say hi, feel free to send me a message.
          </p>

          <q-list dark separator>
            <q-item clickable v-ripple :href="'mailto:' + contactInfo.email">
              <q-item-section avatar>
                <q-icon color="white" name="mdi-email" />
              </q-item-section>
              <q-item-section>
                <q-item-label>Email</q-item-label>
                <q-item-label caption class="text-white">{{ contactInfo.email }}</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple :href="contactInfo.linkedin.url" target="_blank">
              <q-item-section avatar>
                <q-icon color="white" name="mdi-linkedin" />
              </q-item-section>
              <q-item-section>
                <q-item-label>LinkedIn</q-item-label>
                <q-item-label caption class="text-white">{{
                  contactInfo.linkedin.handle
                }}</q-item-label>
              </q-item-section>
            </q-item>

            <q-item>
              <q-item-section avatar>
                <q-icon color="white" name="mdi-map-marker" />
              </q-item-section>
              <q-item-section>
                <q-item-label>Location</q-item-label>
                <q-item-label caption class="text-white">Gampaha, Sri Lanka</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </div>

        <!-- Right Column: Contact Form -->
        <div class="col-12 col-md-7">
          <q-form @submit="onSubmit" class="q-gutter-md">
            <q-input
              dark
              color="primary"
              v-model="contactForm.name"
              label="Your Name *"
              lazy-rules
              :rules="[(val) => (val && val.length > 0) || 'Please type your name']"
            >
              <template v-slot:prepend><q-icon name="mdi-account" /></template>
            </q-input>

            <q-input
              dark
              color="primary"
              v-model="contactForm.email"
              label="Your Email *"
              lazy-rules
              :rules="[
                (val) => !!val || 'Email is required',
                (val) => /.+@.+\..+/.test(val) || 'Please enter a valid email',
              ]"
            >
              <template v-slot:prepend><q-icon name="mdi-email" /></template>
            </q-input>

            <q-input dark color="primary" v-model="contactForm.subject" label="Subject">
              <template v-slot:prepend><q-icon name="mdi-format-text" /></template>
            </q-input>

            <q-input
              dark
              color="primary"
              v-model="contactForm.message"
              label="Your Message *"
              type="textarea"
              lazy-rules
              :rules="[(val) => (val && val.length > 0) || 'Please type a message']"
            />

            <div>
              <q-btn
                label="Send Message"
                type="submit"
                color="primary"
                unelevated
                rounded
                class="full-width"
                icon-right="mdi-send"
                :loading="isSubmitting"
              />
            </div>
          </q-form>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()

const contactInfo = ref({
  email: 'behanravishka03@gmail.com',
  linkedin: {
    handle: 'behanravishkaperera',
    url: 'https://www.linkedin.com/in/behanravishkaperera',
  },
  location: 'Colombo, Sri Lanka',
})

const contactForm = ref({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const isSubmitting = ref(false)

const resetForm = () => {
  contactForm.value = { name: '', email: '', subject: '', message: '' }
}

const onSubmit = async () => {
  isSubmitting.value = true

  // --- SIMULATE API CALL ---
  // In a real app, you would send the data to a backend service here.
  // For example, using axios:
  // try {
  //   await axios.post('https://api.yourdomain.com/contact', contactForm.value);
  //   $q.notify(...);
  //   resetForm();
  // } catch (error) {
  //   $q.notify({ type: 'negative', message: 'Something went wrong.'});
  // } finally {
  //   isSubmitting.value = false;
  // }
  // -------------------------

  // For demonstration purposes, we'll use a timeout
  setTimeout(() => {
    $q.notify({
      icon: 'mdi-check-all',
      color: 'positive',
      message: 'Message Sent!',
      caption: 'Thanks for reaching out. I will get back to you shortly.',
    })
    resetForm()
    isSubmitting.value = false
  }, 2000)
}
</script>

<style lang="scss" scoped>
.contact-page {
  background: linear-gradient(-45deg, #0f0c29, #c1c2bf, #0f0c29);
}

.contact-container {
  max-width: 1100px;
  width: 100%;
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
}

.q-item__label--caption {
  color: rgba(255, 255, 255, 0.7) !important;
}

// Responsive adjustments
@media (max-width: $breakpoint-sm-max) {
  .contact-container {
    padding: 24px;
  }
  h2 {
    font-size: 2rem;
  }
}
</style>
