<script setup>
import { ref } from 'vue'

defineProps({
  sections: {
    type: Array,
    required: true
  },
  active: {
    type: String,
    required: true
  }
})

const isOpen = ref(false)

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
  isOpen.value = false
}

function toggleMenu() {
  isOpen.value = !isOpen.value
}
</script>

<template>
  <header class="nav">
    <div class="nav-inner">
      <a class="brand" href="#home" @click.prevent="scrollTo('home')">
        Safira <span>Choirun Nisa'</span>
      </a>

      <!-- Links versi desktop -->
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

      <!-- Tombol hamburger, hanya muncul di mobile -->
      <button
        class="menu-toggle"
        @click="toggleMenu"
        :aria-expanded="isOpen"
        aria-label="Toggle menu"
      >
        <svg v-if="!isOpen" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
          <line x1="3" y1="6" x2="21" y2="6" />
          <line x1="3" y1="12" x2="21" y2="12" />
          <line x1="3" y1="18" x2="21" y2="18" />
        </svg>
        <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
          <line x1="5" y1="5" x2="19" y2="19" />
          <line x1="19" y1="5" x2="5" y2="19" />
        </svg>
      </button>
    </div>

    <!-- Dropdown menu untuk mobile -->
    <transition name="fade-slide">
      <nav v-if="isOpen" class="links-mobile">
        <a
          v-for="s in sections"
          :key="s.id"
          href="#"
          class="link-mobile"
          :class="{ active: active === s.id }"
          @click.prevent="scrollTo(s.id)"
        >
          {{ s.label }}
        </a>
      </nav>
    </transition>
  </header>
</template>

<style scoped>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: rgba(6, 11, 23, 0.78);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--border-subtle);
}

.nav-inner {
  max-width: 1280px;
  margin: 0 auto;
  height: var(--nav-height);
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

/* Hamburger button, disembunyikan di desktop */
.menu-toggle {
  display: none;
  align-items: center;
  justify-content: center;
  width: 38px;
  height: 38px;
  border-radius: 10px;
  background: var(--bg-elevated);
  color: var(--text-primary);
  border: 1px solid var(--border-subtle);
  flex-shrink: 0;
  cursor: pointer;
}

.links-mobile {
  display: none;
}

@media (max-width: 780px) {
  .nav-inner {
    padding: 0 5vw;
  }

  /* Sembunyikan strip horizontal, ganti dengan hamburger */
  .links {
    display: none;
  }
  .menu-toggle {
    display: flex;
  }

  .links-mobile {
    display: flex;
    flex-direction: column;
    padding: 8px 5vw 18px;
    gap: 2px;
    background: rgba(6, 11, 23, 0.97);
    border-bottom: 1px solid var(--border-subtle);
  }

  .link-mobile {
    padding: 12px 14px;
    border-radius: 10px;
    font-size: 0.92rem;
    font-weight: 500;
    color: var(--text-secondary);
    transition: color 0.2s ease, background 0.2s ease;
  }

  .link-mobile.active {
    color: var(--blue-accent-soft);
    background: var(--bg-elevated);
  }

  .brand span {
    display: none;
  }
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-6px);
}
</style>