<template>
  <q-page class="about-page flex flex-center q-pa-md">
    <div class="about-container bg-grey-10 q-pa-xl rounded-borders shadow-2">
      <div class="row items-center q-col-gutter-xl">
        <!-- Animated Profile Image -->
        <div class="col-12 col-md-4 text-center">
          <div class="image-container">
            <div class="image-wrapper">
              <q-img
                src="src/images/profile.png"
                alt="Behan Ravishka Perera"
                class="profile-image"
                ratio="1"
              />
            </div>
          </div>
        </div>

        <!-- About Me Text and Details -->
        <div class="col-12 col-md-8">
          <div class="text-overline text-grey-5">Software Engineering Undergraduate</div>
          <h1 class="text-h3 text-weight-bold q-my-sm text-white">M P Behan Ravishka Perera</h1>
          <p class="text-subtitle1 text-white q-mb-sm">
            A future Tech Enthusiast combining logic with creativity.
          </p>

          <q-separator dark class="q-my-lg" />

          <p class="text-body1 text-grey-4" loading="lazy">
            Hi, I’m Behan, a Software Engineering undergraduate at Sir John Kotelawala Defence
            University (KDU). With strong technical foundations in programming and designing, I
            enjoy combining logical thinking with creativity to build practical and user-friendly
            solutions.
          </p>
          <p class="text-body1 text-grey-4" loading="lazy">
            I'm especially interested in web development and database systems, and I'm always
            looking to expand my skills through hands-on projects. I’ve taken part in several IT
            industry-related workshops, which helped me gain valuable insights into how technology
            is applied in the real world. These experiences also strengthened my teamwork and
            problem-solving abilities in high-pressure environments.
          </p>

          <q-separator dark class="q-my-lg" />

          <!-- Interests & Skills Section -->
          <div class="q-mb-md" loading="lazy">
            <h2 class="text-h6 text-weight-medium text-white q-mb-sm">Interests & Skills</h2>
            <div class="q-gutter-sm">
              <q-chip
                v-for="skill in skills"
                :key="skill.name"
                :icon="skill.icon"
                :color="skill.color"
                text-color="white"
                clickable
                class="glossy"
              >
                {{ skill.name }}
              </q-chip>
            </div>
          </div>

          <q-separator dark class="q-my-lg" />

          <!-- Connect Section -->
          <div loading="lazy">
            <h2 class="text-h6 text-weight-medium text-white q-mb-sm">Let's Connect</h2>
            <p class="text-body2 text-grey-5">
              I’m eager to connect with professionals in the tech industry, especially in Sri Lanka.
              Let's explore opportunities where I can contribute, grow, and make a positive impact!
            </p>
            <div class="q-gutter-sm">
              <q-btn
                v-for="link in socialLinks"
                :key="link.name"
                :icon="link.icon"
                :href="link.url"
                target="_blank"
                round
                unelevated
                :color="link.color"
                :aria-label="link.name"
              >
                <q-tooltip :class="`bg-${link.color}`">{{ link.name }}</q-tooltip>
              </q-btn>
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const skills = ref([
  { name: 'Web Development', icon: 'mdi-web', color: 'primary' },
  { name: 'Database Systems', icon: 'mdi-database', color: 'blue' },
  { name: 'UI/UX Design', icon: 'mdi-palette-swatch', color: 'grey' },
  { name: 'Problem Solving', icon: 'mdi-lightbulb-on-outline', color: 'orange' },
  { name: 'Teamwork', icon: 'mdi-account-group', color: 'green' },
  { name: 'Digital Transformation', icon: 'mdi-chart-donut', color: 'purple' },
])

const socialLinks = ref([
  {
    name: 'LinkedIn',
    icon: 'mdi-linkedin',
    url: 'https://www.linkedin.com/in/behanravishkaperera',
    color: 'blue-8',
  },
  { name: 'GitHub', icon: 'mdi-github', url: 'https://github.com/Behan-Ravishka', color: 'grey-8' },
  { name: 'Email Me', icon: 'mdi-email', url: 'mailto:behanravishka03@gmail.com', color: 'red-8' },
  {
    name: 'Portfolio',
    icon: 'mdi-briefcase',
    url: 'https://behanravishka.42web.io/?i=2',
    color: 'teal-8',
  },
])
</script>

<style lang="scss" scoped>
.about-page {
  background: linear-gradient(-45deg, #0f0c29, #c1c2bf, #0f0c29);
}

.about-container {
  max-width: 1200px;
  width: 100%;
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
}

.image-container {
  position: relative;
  width: 250px;
  height: 250px;
  margin: 0 auto;
  padding: 5px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;

  // The rotating gradient border
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 50%;
    background: conic-gradient(from 0deg, #89ff00, #00bcd4, #ff00ff, #ffc107, #89ff00);
    animation: rotate 4s linear infinite;
    z-index: -1;
    opacity: 0.6;
    transition: opacity 0.3s ease-in-out;
  }

  &:hover::before {
    animation-duration: 2s;
    opacity: 1;
  }
}

// Keyframes for the rotation animation
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.image-wrapper {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden; /* This clips the q-img into a circle */
  background: #1d1d1d;
  box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.5);
}

.profile-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);

  &:hover {
    transform: scale(1.1);
  }
}

h1,
h2 {
  line-height: 1.2;
}

// Responsive adjustments
@media (max-width: $breakpoint-sm-max) {
  .about-container {
    padding: 24px;
  }
  h1 {
    font-size: 2.5rem;
  }
  .image-container {
    width: 200px;
    height: 200px;
    margin-bottom: 24px;
  }
}
</style>
