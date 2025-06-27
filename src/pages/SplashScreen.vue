<template>
  <q-page class="column flex-center bg-white">
    <div
      class="text-h4 font-impact text-primary animate__animated animate__fadeInDown"
      style="font-family: Impact, Charcoal, sans-serif; font-weight: bold"
    >
      Welcome to My Portfolio..!
    </div>
    <q-spinner-tail color="primary" size="40px" class="q-mt-md" />
  </q-page>
</template>

<script>
export default {
  mounted() {
    // Navigate to real home page after 2 seconds
    setTimeout(() => {
      this.$router.replace('/home')
    }, 2000)
  },
}
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css';
</style>
