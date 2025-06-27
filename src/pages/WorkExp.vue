<template>
  <q-page class="q-pa-md bg-grey-2">
    <div class="text-h4 text-center q-mb-xl text-primary">💼 Work Experience</div>
    <div class="q-timeline">
      <q-timeline-entry
        v-for="exp in experiences"
        :key="exp.title"
        :title="exp.title"
        :subtitle="exp.company"
        :side="exp.side"
        :color="exp.color"
        :icon="exp.icon"
      >
        <div class="text-body2 text-grey-8 q-mb-sm">{{ exp.period }}</div>
        <ul>
          <li v-for="duty in exp.duties" :key="duty">{{ duty }}</li>
        </ul>
      </q-timeline-entry>
    </div>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      experiences: [
        {
          title: 'Frontend Developer',
          company: 'ABC Software Solutions',
          period: 'Jan 2023 - Present',
          duties: [
            'Built responsive web UIs using Vue + Quasar',
            'Integrated REST APIs and optimized performance',
            'Collaborated with UX teams to improve design flow',
          ],
          side: 'left',
          color: 'primary',
          icon: 'work',
        },
        {
          title: 'Intern - Web Development',
          company: 'Startup Inc.',
          period: 'Jun 2022 - Dec 2022',
          duties: [
            'Assisted in UI design and bug fixing',
            'Built components and animations',
            'Learned Agile & Git-based workflows',
          ],
          side: 'right',
          color: 'secondary',
          icon: 'school',
        },
        // Add more experiences if needed
      ],
    }
  },
}
</script>

<style scoped>
ul {
  padding-left: 1.2rem;
}
li {
  margin-bottom: 6px;
}
</style>
