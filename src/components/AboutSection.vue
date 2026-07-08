<script setup>
import AppIcon from './AppIcon.vue'
const socials = [
  { brand: 'instagram', label: 'Instagram', href: 'https://www.instagram.com/safiracn_', image: '/images/ig.webp' },
  { brand: 'github', label: 'GitHub', href: 'https://github.com/safiracn' },
  { brand: 'linkedin', label: 'LinkedIn', href: 'https://www.linkedin.com/in/safiracn' }
]
</script>

<template>
  <section id="about" class="section about">
    <div class="section-inner about-inner">
      <div class="about-text">
        <p class="eyebrow">About</p>
        <h2 class="section-title">A little about me</h2>

        <p class="about-desc">
          Undergraduate Information System Student, Faculty of Computer Science, with a genuine passion for data analytics and fullstack development, backed by a solid foundation in database systems, application development, and business process analysis built through hands on projects and real world problem solving. I actively seek new challenges rather than waiting for them to come, adapting quickly to unfamiliar tools, technologies, and team environments, and approaching every unfamiliar dataset or situation with curiosity and a strong willingness to learn. Actively involved in campus organizations and committees, I have sharpened my communication, teamwork, and problem solving abilities alongside my technical skills, and I believe real impact comes from combining strong execution with openness to feedback and continuous growth. For me, every project and every new environment is an opportunity to turn data into clear insights, build functional and reliable applications, and deliver measurable impact.
        </p>

      <div class="socials">
        <a
          v-for="s in socials"
          :key="s.label"
          class="social-icon"
          :href="s.href"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="s.label"
        >
          <img
            v-if="s.image"
            :src="s.image"
            :alt="s.label"
            class="social-img"
          />

          <AppIcon
            v-else
            :brand="s.brand"
            :size="42"
          />
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

.social-icon {
  display: inline-flex;
  transition: transform 0.2s ease, filter 0.2s ease;
}

.social-icon:hover {
  transform: translateY(-4px);
  filter: brightness(1.1);
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

.social-icon {
  width: 50px;
  height: 50px;

  display: flex;
  align-items: center;
  justify-content: center;

  transition: transform .2s ease, filter .2s ease;
}

.social-img {
  width: 50px;
  height: 50px;
  display: block;
  object-fit: contain;
}

</style>
