<template>
  <q-page class="q-pa-md bg-grey-1">
    <div class="text-h4 text-center q-mb-md text-primary">🚀 My Projects</div>
    <q-card flat bordered class="q-pa-md bg-white shadow-3">
      <q-input v-model="search" label="Search Projects" dense outlined clearable />
    </q-card>

    <div class="q-gutter-md row q-mt-lg justify-center">
      <q-card
        v-for="project in filteredProjects"
        :key="project.id"
        class="my-card col-xs-12 col-sm-6 col-md-4"
        @click="openDialog(project)"
        flat
        bordered
        style="cursor: pointer"
      >
        <q-img :src="project.image" :alt="project.title" ratio="16/9" class="project-image">
          <div class="absolute-bottom bg-primary text-white text-subtitle2 q-pa-sm">
            {{ project.title }}
          </div>
        </q-img>
      </q-card>
    </div>

    <q-dialog v-model="dialog">
      <q-card style="max-width: 600px; width: 100%">
        <q-img :src="selected.image" />
        <q-card-section>
          <div class="text-h6">{{ selected.title }}</div>
          <div class="text-subtitle2 text-grey-7">{{ selected.description }}</div>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn flat label="Close" color="primary" v-close-popup />
          <q-btn :href="selected.link" target="_blank" label="Visit" color="secondary" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      search: '',
      dialog: false,
      selected: {},
      projects: [
        {
          id: 1,
          title: 'FoodShare App',
          image: 'https://source.unsplash.com/featured/?food,app',
          description: 'A mobile app that connects food donors with NGOs.',
          link: 'https://github.com/yourusername/foodshare',
        },
        {
          id: 2,
          title: 'Portfolio Website',
          image: 'https://source.unsplash.com/featured/?portfolio,web',
          description: 'My personal portfolio built with Quasar.',
          link: 'https://yourportfolio.com',
        },
        // Add more projects here...
      ],
    }
  },
  computed: {
    filteredProjects() {
      return this.projects.filter((p) => p.title.toLowerCase().includes(this.search.toLowerCase()))
    },
  },
  methods: {
    openDialog(project) {
      this.selected = project
      this.dialog = true
    },
  },
}
</script>

<style scoped>
.project-image {
  transition: transform 0.3s ease;
}
.project-image:hover {
  transform: scale(1.05);
}
</style>
