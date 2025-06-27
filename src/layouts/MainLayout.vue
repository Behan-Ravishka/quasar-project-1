<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>Simple Portfolio</q-toolbar-title>

        <div>Version 1.0.0</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>- Choose -</q-item-label>

        <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Home',
    caption: 'Home Page',
    icon: 'home',
    link: 'home',
  },
  {
    title: 'About',
    caption: 'About this app',
    icon: 'person',
    link: 'about',
  },
  {
    title: 'Contact',
    caption: 'Contact us',
    icon: 'call',
    link: 'contact',
  },
  {
    title: 'projects',
    caption: 'My Projects',
    icon: 'work',
    link: 'projects',
  },
  {
    title: 'experience',
    caption: 'My Experience',
    icon: 'work_history',
    link: 'work',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
