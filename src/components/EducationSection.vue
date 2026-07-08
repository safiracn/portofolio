<script setup>
const education = [
  {
    school: 'Universitas Pembangunan Nasional "Veteran" Jawa Timur',
    degree: 'Bachelor of Information Systems, Faculty of Computer Science',
    meta: 'GPA 3.87 / 4.00',
    location: 'Surabaya, Indonesia',
    period: 'August 2024 — Present',
    current: true
  },
  {
    school: 'SMAN 1 Wonoayu',
    degree: 'Science and Mathematics Major',
    meta: null,
    location: 'Sidoarjo, Indonesia',
    period: 'June 2021 — June 2024',
    current: false
  }
]
</script>

<template>
  <section id="education" class="section education">
    <div class="section-inner">
      <p class="eyebrow">Education</p>
      <h2 class="section-title">Academic journey</h2>

      <div class="timeline">
        <div class="timeline-line" aria-hidden="true"></div>

        <div
          v-for="(item, i) in education"
          :key="item.school"
          class="timeline-item"
        >
          <div class="timeline-marker" :class="{ current: item.current }">
            <span class="marker-dot"></span>
          </div>

          <div class="timeline-card">
            <div class="card-top">
              <span class="period">{{ item.period }}</span>
              <span v-if="item.current" class="badge-current">Ongoing</span>
            </div>
            <h3 class="school">{{ item.school }}</h3>
            <p class="degree">{{ item.degree }}</p>
            <div class="card-meta">
              <span v-if="item.meta" class="meta-pill">{{ item.meta }}</span>
              <span class="meta-location">{{ item.location }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  position: relative;
  padding-left: 40px;
}

.timeline-line {
  position: absolute;
  left: 7px;
  top: 8px;
  bottom: 8px;
  width: 1.5px;
  background: linear-gradient(180deg, var(--blue-accent), var(--blue-dim) 80%, transparent);
}

.timeline-item {
  position: relative;
  margin-bottom: 36px;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-marker {
  position: absolute;
  left: -40px;
  top: 26px;
  width: 16px;
  height: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.marker-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--bg-deep);
  border: 2px solid var(--blue-dim);
}

.timeline-marker.current .marker-dot {
  background: var(--blue-accent);
  border-color: var(--blue-accent);
  box-shadow: 0 0 0 4px rgba(76, 126, 255, 0.18);
}

.timeline-card {
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  padding: 26px 30px;
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.timeline-card:hover {
  transform: translateX(4px);
  border-color: var(--border-strong);
}

.card-top {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.period {
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  color: var(--blue-accent-soft);
}

.badge-current {
  font-size: 0.7rem;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 999px;
  background: rgba(76, 126, 255, 0.14);
  color: var(--blue-accent-soft);
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.school {
  font-size: 1.15rem;
  font-weight: 600;
  margin-bottom: 6px;
}

.degree {
  font-size: 0.92rem;
  color: var(--text-secondary);
  margin-bottom: 14px;
}

.card-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
}

.meta-pill {
  font-size: 0.78rem;
  font-weight: 600;
  padding: 4px 12px;
  border-radius: 999px;
  background: var(--bg-elevated-2);
  color: var(--text-primary);
}

.meta-location {
  font-size: 0.82rem;
  color: var(--text-muted);
}

@media (max-width: 640px) {
  .timeline {
    padding-left: 30px;
  }
  .timeline-marker {
    left: -30px;
  }
  .timeline-card {
    padding: 20px 22px;
  }
}
</style>
