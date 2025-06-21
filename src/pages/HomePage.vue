<template>
  <q-page class="home-page flex flex-center text-center text-white q-pa-md">
    <div class="hero-content">
      <div class="text-overline text-white-5">SOFTWARE ENGINEERING UNDERGRADUATE</div>

      <div class="row items-center justify-center q-col-gutter-md q-my-md animate-fade-in-down">
        <!-- This column holds the avatar. It stacks on mobile. -->
        <div class="col-12 col-sm-auto">
          <q-avatar size="100px">
            <img src="src/images/profile.png" alt="profile photo" />
          </q-avatar>
        </div>

        <!-- This column holds the H1 text. -->
        <div class="col-12 col-sm-auto">
          <h1 class="text-h2 text-weight-bold no-margin text-center text-sm-left">
            Hi, I'm Behan Perera
          </h1>
        </div>
      </div>

      <div class="text-h5 text-white q-mb-xl animate-fade-in-up">
        <span>{{ typedText }}</span>
        <span class="typing-cursor">|</span>
      </div>

      <p
        class="text-body1 text-grey-5 q-mb-xl"
        style="max-width: 600px; margin-left: auto; margin-right: auto"
      >
        I combine logical thinking with creativity to build practical, user-friendly, and impactful
        digital solutions.
      </p>

      <div class="q-gutter-md animate-fade-in-up">
        <q-btn
          to="/about"
          label="About Me"
          color="primary"
          size="lg"
          unelevated
          rounded
          icon="mdi-account-circle-outline"
        />
        <q-btn
          to="/contact"
          label="Get in Touch"
          color="white"
          text-color="white"
          outline
          rounded
          size="lg"
          icon-right="mdi-send-outline"
        />
      </div>
      <div class="explore-section animate-fade-in-up">
        <q-separator
          dark
          class="q-my-xl"
          style="max-width: 250px; margin-left: auto; margin-right: auto"
        />

        <h2 class="text-h4 text-weight-medium">Explore My Work</h2>
        <p
          class="text-body1 text-grey-5"
          style="max-width: 500px; margin-left: auto; margin-right: auto"
        >
          Here's a glimpse into the projects I've built and the skills I've gained. See how I turn
          ideas into reality.
        </p>

        <div class="q-gutter-md q-mt-lg">
          <q-btn
            to="/projects"
            label="View Projects"
            color="primary"
            unelevated
            rounded
            size="lg"
            icon="mdi-code-braces"
          />
          <q-btn
            to="/work"
            label="Work Experience"
            color="primary"
            unelevated
            rounded
            size="lg"
            icon="mdi-briefcase-variant-outline"
          />
        </div>
      </div>

      <q-separator dark class="q-my-xl" />

      <div class="text-h4 text-weight-medium q-mb-md">Connect with Me</div>
      <p class="text-body1 text-grey-5 q-mb-lg">
        I'm always open to new opportunities and collaborations. Let's connect and create something
        amazing together!
      </p>

      <div class="q-gutter-md q-mb-lg">
        <q-btn
          to="/contact"
          label="Contact Me"
          color="primary"
          unelevated
          rounded
          size="md"
          icon="mdi-email-outline"
        />
      </div>

      <q-separator dark class="q-my-lg" />

      <div class="text-center text-grey-5 q-mt-lg">
        <p class="text-caption">© 2025 Behan Ravishka Perera. All rights reserved!</p>
        <p class="text-caption">Built using Vue.js and Quasar Framework.</p>
      </div>
    </div>
    <q-img
      src="src/images/bg.png"
      class="absolute-full"
      style="opacity: 0.08; z-index: -1"
      contain
      cover
      position="center"
      loading="lazy"
      alt="Background Image"
    />
  </q-page>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// --- Configuration for the Looping Typewriter ---
const phrases = [
  'Building Digital Experiences',
  'A Passionate Tech Enthusiast',
  'Solving Problems with Code',
  'Creative and Logical Thinker',
]
const typingSpeed = 100
const erasingSpeed = 50
const newPhraseDelay = 2000

// --- Reactive State Variables ---
const typedText = ref('')
const phraseIndex = ref(0)
const charIndex = ref(0)
const isTyping = ref(true)
let timeoutId = null // To hold the timeout ID for cleanup

const typewriterEffect = () => {
  // Clear any existing timeout
  if (timeoutId) clearTimeout(timeoutId)

  const currentPhrase = phrases[phraseIndex.value]
  let delay = isTyping.value ? typingSpeed : erasingSpeed

  if (isTyping.value) {
    // --- Typing Logic ---
    if (charIndex.value < currentPhrase.length) {
      typedText.value += currentPhrase.charAt(charIndex.value)
      charIndex.value++
    } else {
      // Finished typing, switch to erasing after a pause
      isTyping.value = false
      delay = newPhraseDelay
    }
  } else {
    // --- Erasing Logic ---
    if (charIndex.value > 0) {
      typedText.value = currentPhrase.substring(0, charIndex.value - 1)
      charIndex.value--
    } else {
      // Finished erasing, switch to typing the next phrase
      isTyping.value = true
      phraseIndex.value = (phraseIndex.value + 1) % phrases.length
    }
  }

  // Set the next timeout
  timeoutId = setTimeout(typewriterEffect, delay)
}

// --- Lifecycle Hooks ---
onMounted(() => {
  timeoutId = setTimeout(typewriterEffect, 500)
})

onUnmounted(() => {
  // IMPORTANT: Clean up the timeout when the component is unmounted
  clearTimeout(timeoutId)
})
</script>

<style lang="scss" scoped>
.home-page {
  background: linear-gradient(-45deg, #0f0c29, #dedfdc, #0f0c29);
  background-size: 400% 400%;
  animation: gradientAnimation 15s ease infinite;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: auto;
  color: white;
  text-align: center;
  padding: 2rem;
  overflow: hidden;
  position: relative;
  z-index: 1;
}

.hero-content {
  max-width: 800px;
}

h1 {
  font-size: 4.5rem;
  line-height: 1.1;
  letter-spacing: -1.5px;
}

// Typing cursor animation
.typing-cursor {
  display: inline-block;
  font-weight: 300;
  animation: blink 0.7s infinite;
}

@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

// Simple entrance animations
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translate3d(0, -30px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 30px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.animate-fade-in-down {
  animation: fadeInDown 0.8s ease-out both;
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out 0.4s both; // 0.4s delay
}

// Responsive adjustments
@media (max-width: $breakpoint-md-max) {
  h1 {
    font-size: 3.5rem;
  }
}

@media (max-width: $breakpoint-sm-max) {
  h1 {
    font-size: 2.75rem;
  }
  .text-h5 {
    font-size: 1.25rem;
  }
}
</style>
