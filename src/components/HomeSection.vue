<script setup>
import AppIcon from './AppIcon.vue'
function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section id="home" class="section hero">
    <div class="hero-bg" aria-hidden="true">
      <div class="glow glow-a"></div>
      <div class="glow glow-b"></div>
      <div class="grid-dots"></div>
    </div>

    <div class="section-inner hero-inner">
      <p class="hero-eyebrow">Hello, Welcome To My Portfolio👋</p>

      <h1 class="hero-name">Safira Choirun Nisa'</h1>

      <p class="hero-role">Undergraduate Information System Student | Faculty of Computer Science</p>
      <p class="hero-focus">Data Analytics &amp; Fullstack Development Enthusiast</p>

      <div class="hero-actions">
        <!-- NOTE: replace the href below with the actual path to your CV file -->
      <a class="btn btn-primary" href="/cv/cv.pdf" download>
        <AppIcon name="download" :size="18" />
        Download CV
      </a>
      <a class="btn btn-ghost" href="#about" @click.prevent="scrollTo('about')">
        <AppIcon name="users" :size="18" />
        About Me
      </a>
      </div>

      <div class="hero-stats">
        <a class="stat-card" href="#projects" @click.prevent="scrollTo('projects')">
          <span class="stat-number">10</span>
          <span class="stat-label">Projects Built</span>
        </a>
        <a class="stat-card" href="#organization" @click.prevent="scrollTo('organization')">
          <span class="stat-number">15+</span>
          <span class="stat-label">Non-Academic Experiences</span>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  align-items: center;
  text-align: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}

.glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(90px);
  opacity: 0.35;
}

.glow-a {
  width: 460px;
  height: 460px;
  background: var(--blue-accent);
  top: -140px;
  left: 8%;
}

.glow-b {
  width: 380px;
  height: 380px;
  background: #2a4fd6;
  bottom: -140px;
  right: 6%;
  opacity: 0.28;
}

.grid-dots {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(var(--blue-dim) 1px, transparent 1px);
  background-size: 26px 26px;
  mask-image: radial-gradient(ellipse 60% 50% at 50% 40%, black 40%, transparent 90%);
  opacity: 0.5;
}

.hero-inner {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hero-eyebrow {
  font-size: 0.82rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--blue-accent-soft);
  margin-bottom: 22px;
}

.hero-name {
  font-size: clamp(2.4rem, 6vw, 4.4rem);
  font-weight: 700;
  letter-spacing: -0.02em;
  line-height: 1.08;
  background: linear-gradient(180deg, #ffffff 0%, var(--blue-accent-soft) 120%);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.hero-role {
  margin-top: 22px;
  font-size: clamp(1rem, 2vw, 1.2rem);
  font-weight: 500;
  color: var(--text-primary);
}

.hero-focus {
  margin-top: 8px;
  font-size: clamp(0.92rem, 1.6vw, 1.02rem);
  font-weight: 400;
  color: var(--text-secondary);
}

.hero-actions {
  margin-top: 40px;
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  justify-content: center;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 9px;
  padding: 13px 28px;
  border-radius: 999px;
  font-size: 0.92rem;
  font-weight: 600;
  transition: transform 0.2s ease, background 0.2s ease, border-color 0.2s ease;
}

.btn-primary {
  background: var(--blue-accent);
  color: #06101f;
}

.btn-primary:hover {
  transform: translateY(-2px);
  background: var(--blue-accent-soft);
}

.btn-ghost {
  border: 1px solid var(--border-strong);
  color: var(--text-primary);
  background: transparent;
}

.btn-ghost:hover {
  transform: translateY(-2px);
  background: var(--bg-elevated);
}

.hero-stats {
  margin-top: 56px;
  display: flex;
  gap: 18px;
  flex-wrap: wrap;
  justify-content: center;
}

.stat-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  min-width: 180px;
  padding: 22px 28px;
  border-radius: var(--radius-md);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.stat-card:hover {
  transform: translateY(-4px);
  border-color: var(--border-strong);
  background: var(--bg-elevated);
}

.stat-number {
  font-size: 1.9rem;
  font-weight: 700;
  color: var(--blue-accent-soft);
}

.stat-label {
  font-size: 0.82rem;
  color: var(--text-secondary);
  font-weight: 500;
}

@media (max-width: 640px) {
  .hero-stats {
    flex-direction: column;
    width: 100%;
  }
  .stat-card {
    width: 100%;
  }
}
</style>
