<script setup>
defineProps({
  sections: {
    type: Array,
    required: true // [{ id, label }]
  },
  active: {
    type: String,
    required: true
  }
})

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <header class="nav">
    <div class="nav-inner">
      <a class="brand" href="#home" @click.prevent="scrollTo('home')">
        Safira <span>Choirun Nisa'</span>
      </a>

      <nav class="links">
        <a
          v-for="s in sections"
          :key="s.id"
          href="#"
          class="link"
          :class="{ active: active === s.id }"
          @click.prevent="scrollTo(s.id)"
        >
          {{ s.label }}
        </a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: var(--nav-height);
  z-index: 100;
  background: rgba(6, 11, 23, 0.78);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--border-subtle);
}

.nav-inner {
  max-width: 1280px;
  margin: 0 auto;
  height: 100%;
  padding: 0 6vw;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

.brand {
  font-weight: 600;
  font-size: 1.02rem;
  color: var(--text-primary);
  white-space: nowrap;
  letter-spacing: -0.01em;
}

.brand span {
  color: var(--blue-accent-soft);
  font-weight: 400;
}

.links {
  display: flex;
  align-items: center;
  gap: 4px;
  overflow-x: auto;
  scrollbar-width: none;
}

.links::-webkit-scrollbar {
  display: none;
}

.link {
  position: relative;
  font-size: 0.88rem;
  font-weight: 500;
  color: var(--text-secondary);
  padding: 8px 14px;
  border-radius: 999px;
  white-space: nowrap;
  transition: color 0.2s ease, background 0.2s ease;
}

.link:hover {
  color: var(--text-primary);
}

.link.active {
  color: var(--blue-accent-soft);
  background: var(--bg-elevated);
}

@media (max-width: 780px) {
  .nav-inner {
    padding: 0 5vw;
  }
  .links {
    gap: 0;
  }
  .link {
    padding: 8px 10px;
    font-size: 0.8rem;
  }
  .brand span {
    display: none;
  }
}
</style>
