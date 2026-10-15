<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)
const logoSrc = '/src/logo-studielink.gif' // put your GIF at public/logo.gif

const categories = [
  { id: 'programmes', type: 'lines', icon: '✓⃝', title: 'Study programmes',
    lines: ['Tilburg University', 'MSc Cognitive Science and Artificial Intelligence', 'Academic year · 2026–2027', 'Status: Enrolled'] },
  { id: 'education', type: 'lines', icon: '🏛️', title: 'Previous education',
    lines: ['Master of Science', 'Erasmus University Rotterdam · Completed 2024', 'Bachelor of Science', 'University of Example · Completed 2022'] },
  { id: 'messages', type: 'messages', icon: '✉️', title: 'Messages',
    messages: [
      { title: 'Your enrolment request has been received', date: '12 October 2026', status: 'Fictional message' },
      { title: 'Check your previous education', date: '10 October 2026', status: 'Fictional message' },
      { title: 'Payment obligation fulfilled', date: 'July 22, 2025', status: 'Unopened message' },
      { title: 'Confirmation of digital authorisation', date: 'July 22, 2025', status: 'Unopened message' },
      { title: 'New To do action-item: enter payment details', date: 'July 9, 2025', status: 'Unopened message' },
      { title: 'Now re-enrol for next year', date: 'May 19, 2025', status: 'Unopened message' },
      { title: 'Payment obligation fulfilled', date: 'July 17, 2024', status: 'Unopened message' },
      { title: 'Authorisation confirmed', date: 'July 17, 2024', status: 'Unopened message' },
    ] },
  { id: 'details', type: 'groups', icon: '👤', title: 'Details',
    groups: [
      { title: 'Contact details', fields: [
        { label: 'Email address', value: 'andrei.oprea2000@yahoo.com' },
        { label: 'Telephone number', value: '+31 6 12345678' },
        { label: 'Correspondence language', value: 'English' } ] },
      { title: 'Personal details', fields: [
        { label: 'Logged in as', value: 'Andrei Oprea' },
        { label: 'Date of birth', value: 'May 10, 2000' } ] },
      { title: 'Current home address', fields: [
        { label: 'Street', value: 'Bomansplaats' }, { label: 'House number', value: '80' },
        { label: 'Addition', value: '—' }, { label: 'Postal code', value: '5611NT' },
        { label: 'Town/city', value: 'EINDHOVEN' }, { label: 'Country', value: 'Netherlands' } ] },
      { title: 'Correspondence address', fields: [
        { label: 'Street', value: 'Bomansplaats' }, { label: 'House number', value: '80' },
        { label: 'Addition', value: '—' }, { label: 'Postal code', value: '5611NT' },
        { label: 'Town/city', value: 'EINDHOVEN' }, { label: 'Country', value: 'Netherlands' } ] },
    ] },
]
</script>

<template>
  <div class="site-shell">
    <div class="top-bar">
      <div class="top-inner">
        <button class="top-action">Help</button>
        <div class="top-right">
          <button class="top-action">Nederland <span class="caret">⌄</span></button>
          <button class="top-action">Deutsch</button>
          <button class="top-action logout"><span class="logout-x">×</span> Log out</button>
        </div>
      </div>
    </div>

    <header class="brand-bar">
      <a class="brand" href="#top" aria-label="Home">
        <img class="logo-img" :src="logoSrc" alt="Logo" />
      </a>
      <button class="hamburger" :aria-expanded="menuOpen" aria-label="Toggle menu" @click="menuOpen = !menuOpen">
        <span></span><span></span><span></span>
      </button>
    </header>

    <nav v-if="menuOpen" class="menu-panel" aria-label="Page navigation">
      <a v-for="c in categories" :key="c.id" :href="'#' + c.id" @click="menuOpen = false">{{ c.title }}</a>
    </nav>

    <main id="top" class="page-content">
      <!-- <div class="page-heading">
        <p class="eyebrow">STUDENT PORTAL · SAMPLE DATA</p>
        <h1>My study overview</h1>
        <p class="intro">Your study information at a glance.</p>
      </div> -->

      <section class="category-list" aria-label="Student information">
        <article v-for="c in categories" :id="c.id" :key="c.id" class="category-card">
          <div class="category-icon" aria-hidden="true">{{ c.icon }}</div>
          <div class="card-heading"><h2>{{ c.title }}</h2></div>

          <div class="card-body">
            <template v-if="c.type === 'lines'">
              <p v-for="(line, i) in c.lines" :key="i" :class="{ 'sub-line': i % 2 === 1 }">{{ line }}</p>
              <button v-if="c.id === 'programmes'" class="terminate-button" type="button">Terminate enrolment</button>
            </template>

            <template v-else-if="c.type === 'messages'">
              <ul class="message-list">
                <li v-for="(m, i) in c.messages" :key="i" class="message-item">
                  <span class="message-title">{{ m.title }}</span>
                  <span class="message-meta">{{ m.date }} · {{ m.status }}</span>
                </li>
              </ul>
            </template>

            <template v-else-if="c.type === 'groups'">
              <section v-for="g in c.groups" :key="g.title" class="detail-group">
                <h3>{{ g.title }}</h3>
                <dl>
                  <div v-for="f in g.fields" :key="f.label" class="detail-row">
                    <dt>{{ f.label }}</dt><dd>{{ f.value }}</dd>
                  </div>
                </dl>
              </section>
            </template>
          </div>
        </article>
      </section>

    </main>
  </div>
</template>
