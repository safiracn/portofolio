<script setup>
const socials = [
  { label: 'Instagram', href: 'https://www.instagram.com/safiracn_' },
  { label: 'GitHub', href: 'https://github.com/safiracn' },
  { label: 'LinkedIn', href: 'https://www.linkedin.com/in/safiracn' }
]
</script>

<template>
  <section id="about" class="section about">
    <div class="section-inner about-inner">
      <div class="about-text">
        <p class="eyebrow">About</p>
        <h2 class="section-title">A little about me</h2>

        <p class="about-desc">
          Information Systems undergraduate at UPN "Veteran" East Java with a solid
          foundation in database systems, application development, and data-driven
          problem solving. Experienced in SQL, cross-platform programming, and
          business process analysis, I am eager to contribute as a data analyst or
          fullstack developer intern. Proactive, detail-oriented, and adaptable, I am
          ready to translate data into clear insights, build functional applications,
          and deliver measurable impact through strong technical execution and
          teamwork.
        </p>

        <div class="socials">
          <a
            v-for="s in socials"
            :key="s.label"
            class="social-pill"
            :href="s.href"
            target="_blank"
            rel="noopener noreferrer"
          >
            {{ s.label }}
          </a>
        </div>
      </div>

      <div class="about-photo-wrap">
        <div class="photo-decor" aria-hidden="true">
          <div class="ring ring-1"></div>
          <div class="ring ring-2"></div>
          <div class="blob"></div>
          <div class="dots"></div>
        </div>
          
        <div class="photo-placeholder">
          <span></span>
          <img src="/images/foto.png" alt="Safira Choirun Nisa'" />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-inner {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  gap: 64px;
  align-items: center;
}

.about-desc {
  font-size: 1rem;
  line-height: 1.85;
  color: var(--text-secondary);
  max-width: 560px;
}

.socials {
  margin-top: 32px;
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.social-pill {
  padding: 10px 22px;
  border-radius: 999px;
  border: 1px solid var(--border-subtle);
  font-size: 0.86rem;
  font-weight: 500;
  color: var(--text-primary);
  background: var(--bg-surface);
  transition: transform 0.2s ease, border-color 0.2s ease, color 0.2s ease;
}

.social-pill:hover {
  transform: translateY(-3px);
  border-color: var(--blue-accent);
  color: var(--blue-accent-soft);
}

.about-photo-wrap {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 380px;
}

.photo-decor {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.ring {
  position: absolute;
  border-radius: 50%;
  border: 1.5px solid var(--border-strong);
}

.ring-1 {
  width: 320px;
  height: 320px;
  top: 8%;
  left: 50%;
  transform: translateX(-50%);
}

.ring-2 {
  width: 240px;
  height: 240px;
  bottom: 4%;
  left: 42%;
  border-color: var(--blue-dim);
}

.blob {
  position: absolute;
  width: 300px;
  height: 300px;
  top: 18%;
  left: 50%;
  transform: translateX(-50%);
  background: radial-gradient(circle, var(--blue-accent) 0%, transparent 70%);
  opacity: 0.3;
  filter: blur(50px);
  border-radius: 50%;
}

.dots {
  position: absolute;
  width: 140px;
  height: 140px;
  right: 4%;
  bottom: 10%;
  background-image: radial-gradient(var(--blue-accent-soft) 1.5px, transparent 1.5px);
  background-size: 16px 16px;
  opacity: 0.4;
}

.photo-placeholder {
  position: relative;
  z-index:1;
  width: 450px;
  height: 540px;
  border-radius: var(--radius-lg);
  background: transparent;
  
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.photo-placeholder span {
  font-size: 0.85rem;
  color: var(--text-muted);
  padding: 0 20px;
}

@media (max-width: 860px) {
  .about-inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }
  .about-photo-wrap {
    order: -1;
    min-height: 300px;
  }
  .photo-placeholder {
    width: 240px;
    height: 270px;
  }
}
</style>
