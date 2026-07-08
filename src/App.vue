<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import NavBar from './components/NavBar.vue'
import HomeSection from './components/HomeSection.vue'
import AboutSection from './components/AboutSection.vue'
import EducationSection from './components/EducationSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import PublicationBlogSection from './components/PublicationBlogSection.vue'
import OrganizationCommitteeSection from './components/OrganizationCommitteeSection.vue'
import ContactSection from './components/ContactSection.vue'

// NOTE: add more entries here as new sections are built
// (Projects, Publication & Blog, Organization & Committee, Contact)
const navSections = [
  { id: 'home', label: 'Home' },
  { id: 'about', label: 'About' },
  { id: 'education', label: 'Education' },
  { id: 'skills', label: 'Skills' },
  { id: 'projects', label: 'Projects' },
  { id: 'publication', label: 'Publication & Blog' },
  { id: 'organization', label: 'Organization & Committee' },
  { id: 'contact', label: 'Contact' }  
]

const activeSection = ref('home')
let observer = null

onMounted(() => {
  const options = {
    root: null,
    rootMargin: '-40% 0px -55% 0px',
    threshold: 0
  }

  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.id
      }
    })
  }, options)

  navSections.forEach((s) => {
    const el = document.getElementById(s.id)
    if (el) observer.observe(el)
  })
})

onBeforeUnmount(() => {
  if (observer) observer.disconnect()
})
</script>

<template>
  <div class="app">
    <NavBar :sections="navSections" :active="activeSection" />

    <main>
      <HomeSection />
      <AboutSection />
      <EducationSection />
      <SkillsSection />
       <ProjectsSection />
       <PublicationBlogSection />
       <OrganizationCommitteeSection />
       <ContactSection />
    </main>

    <footer class="footer">
      <p>&copy; 2026 by Safira Choirun Nisa'</p>
    </footer>
  </div>
</template>

<style scoped>
.footer {
  padding: 32px 8vw 40px;
  text-align: center;
  border-top: 1px solid var(--border-subtle);
}

.footer p {
  font-size: 0.82rem;
  color: var(--text-muted);
}
</style>
