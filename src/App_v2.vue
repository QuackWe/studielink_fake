<script setup>
import { ref } from 'vue'
const menuOpen = ref(false)
const categories = [
  {
    id: 'programmes',
    icon: '✔️',
    title: 'Study programmes',
    lines: [
      'Tilburg University',
      'MSc Cognitice Science and Artificial Intelligence',
      'Academic year · 2026–2027',
      'Status: Enrolled',
    ],
  },
  {
    id: 'education',
    icon: '📖',
    title: 'Previous education',
    lines: [
      'Master of Science',
      'Erasmus University Rotterdam · Completed 2024',
      'Bachelor of Science',
      'University of Example · Completed 2022',
    ],
  },
  {
    id: 'messages',
    icon: '✉️',
    title: 'Messages',
    messages: [
      { title: 'Your enrolment request has been received', date: '12 October 2026', status: 'Fictional message' },
      { title: 'Check your previous education', date: '10 October 2026', status: 'Fictional message' },
      { title: 'Payment obligation fulfilled', date: 'July 22, 2025', status: 'Unopened message' },
      { title: 'Confirmation of digital authorisation', date: 'July 22, 2025', status: 'Unopened message' },
      { title: 'New To do action-item: enter payment details', date: 'July 9, 2025', status: 'Unopened message' },
      { title: 'Now re-enrol for next year', date: 'May 19, 2025', status: 'Unopened message' },
      { title: 'Payment obligation fulfilled', date: 'July 17, 2024', status: 'Unopened message' },
      { title: 'Authorisation confirmed', date: 'July 17, 2024', status: 'Unopened message' },
    ],
  },
  {
    id: 'details',
    icon: '👤',
    title: 'Details',
    groups: [
      {
        title: 'Contact details',
        fields: [
          { label: 'Email address', value: 'andrei.r.oprea00@gmail.com' },
          { label: 'Telephone number', value: '+40724666617' },
          { label: 'Telephone number 2', value: '+31651725163' },
          { label: 'Correspondence language', value: 'English' },
        ],
      },
      {
        title: 'Personal details',
        fields: [
          { label: 'Logged in as', value: 'Rareş Andrei Oprea' },
          { label: 'Latest log in', value: 'October 12, 2026 3:20:59 PM CEST' },
          { label: 'Date of birth', value: 'May 10, 2000' },
        ],
      },
      {
        title: 'Current home address',
        fields: [
          { label: 'Street', value: 'Bomansplaats' },
          { label: 'House number', value: '80' },
          { label: 'Addition', value: '—' },
          { label: 'Postal code', value: '5611NT' },
          { label: 'Town/city', value: 'EINDHOVEN' },
          { label: 'Country', value: 'Netherlands' },
        ],
      },
      {
        title: 'Correspondence address',
        fields: [
          { label: 'Street', value: 'Bomansplaats' },
          { label: 'House number', value: '80' },
          { label: 'Addition', value: '—' },
          { label: 'Postal code', value: '5611NT' },
          { label: 'Town/city', value: 'EINDHOVEN' },
          { label: 'Country', value: 'Netherlands' },
        ],
      },
    ],
  },
]
</script>

<template>
  <div class="site-shell">
    <div class="top-bar"><div class="top-inner"><button class="top-action">Help</button><button class="top-action">Nederland <span class="caret">⌄</span></button><button class="top-action">Deutsch</button><button class="top-action logout"><span class="logout-x">×</span> Log out</button></div></div>
    <header class="brand-bar"><a class="brand" href="#top" aria-label="Student portal mockup home"><span class="logo-placeholder">LOGO PLACEHOLDER</span><span class="mock-tag">FILM MOCKUP</span></a><button class="hamburger" :aria-expanded="menuOpen" aria-label="Toggle menu" @click="menuOpen = !menuOpen"><span></span><span></span><span></span></button></header>
    <nav v-if="menuOpen" class="menu-panel" aria-label="Page navigation"><a v-for="category in categories" :key="category.id" :href="'#' + category.id" @click="menuOpen = false">{{ category.title }}</a></nav>
    <main id="top" class="page-content"><div class="page-heading"><p class="eyebrow">STUDENT PORTAL · SAMPLE DATA</p><h1>My study overview</h1><p class="intro">Your study information at a glance.</p></div>
      <section class="category-list" aria-label="Student information"><article v-for="category in categories" :id="category.id" :key="category.id" class="category-card"><div class="category-icon" aria-hidden="true">{{ category.icon }}</div><div class="card-heading"><h2>{{ category.title }}</h2></div><div class="card-body"><p v-for="(line,index) in category.lines" :key="index" :class="{'sub-line':index % 2 === 1}">{{ line }}</p><button v-if="category.id === 'programmes'" class="terminate-button" type="button">Terminate enrolment</button></div></article></section>
      <footer class="page-footer"><span>FICTIONAL FILM-PROJECT INTERFACE</span><span>Not an official service</span></footer>
    </main>
  </div>
</template>
