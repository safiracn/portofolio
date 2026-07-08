<script setup>
import { ref } from 'vue'

const education = [
  {
    school: 'Universitas Pembangunan Nasional "Veteran" Jawa Timur',
    degree: 'Bachelor of Information Systems, Faculty of Computer Science',
    meta: 'GPA 3.87 / 4.00',
    location: 'Surabaya, Indonesia',
    period: 'August 2024 — Present',
    current: true,
    // Taruh file logo di folder "public/images/upn.png" pada project Vite-mu,
    // baru path "/images/upn.png" ini akan berhasil dimuat
    logo: '/images/upn.png',
    initials: 'UPN'
  },
  {
    school: 'SMAN 1 Wonoayu',
    degree: 'Science and Mathematics Major',
    meta: null,
    location: 'Sidoarjo, Indonesia',
    period: 'June 2021 — June 2024',
    current: false,
    // Sama, taruh di "public/images/smanwonoayu.png"
    logo: '/images/smaniwa.png',
    initials: 'SMA'
  }
]

// Menyimpan status error tiap logo, supaya kalau link gambar gagal load
// otomatis fallback ke inisial (bukan gambar rusak / broken icon)
const logoError = ref(education.map(() => false))

function handleLogoError(i) {
  logoError.value[i] = true
}
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
            <!-- Panggung logo di sisi kanan: glow lembut + logo besar -->
            <div class="logo-stage" aria-hidden="true">
              <div class="logo-glow" :class="{ current: item.current }"></div>
              <div class="logo-frame">
                <img
                  v-if="item.logo && !logoError[i]"
                  :src="item.logo"
                  :alt="item.school + ' logo'"
                  class="logo-img"
                  @error="handleLogoError(i)"
                />
                <span v-else class="logo-fallback">{{ item.initials }}</span>
              </div>
            </div>

            <div class="card-content">
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
  position: relative;
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  padding: 26px 30px;
  overflow: hidden;
  min-height: 168px;
  display: flex;
  align-items: center;
  transition: transform 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease;
}

.timeline-card:hover {
  transform: translateX(4px);
  border-color: var(--border-strong);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.14);
}

.timeline-card:hover .logo-img {
  transform: scale(1.06);
  filter: grayscale(0.1) opacity(1) drop-shadow(0 14px 26px rgba(0, 0, 0, 0.4));
}

.timeline-card:hover .logo-glow {
  opacity: 1;
  transform: scale(1.08);
}

/* --- Panggung logo besar di kanan --- */
.logo-stage {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  width: 230px;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  z-index: 0;
}

.logo-glow {
  position: absolute;
  width: 190px;
  height: 190px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(76, 126, 255, 0.22), transparent 72%);
  filter: blur(4px);
  opacity: 0.85;
  transition: transform 0.35s ease, opacity 0.35s ease;
}

.logo-glow.current {
  background: radial-gradient(circle, rgba(76, 126, 255, 0.38), transparent 72%);
}

.logo-frame {
  position: relative;
  width: 152px;
  height: 152px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo-img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  /* Sentuhan monokrom lembut, tapi detail logo tetap terlihat jelas.
     Hapus baris filter ini kalau ingin logo full warna asli. */
  filter: grayscale(0.35) opacity(0.92) drop-shadow(0 10px 22px rgba(0, 0, 0, 0.35));
  transition: transform 0.35s ease, filter 0.35s ease;
}

.logo-fallback {
  font-size: 3rem;
  font-weight: 800;
  letter-spacing: 0.02em;
  color: var(--blue-accent-soft);
  line-height: 1;
  white-space: nowrap;
  opacity: 0.9;
}

/* Fade halus di tepi kanan supaya logo menyatu rapi dengan tepi kartu */
.timeline-card::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  width: 90px;
  background: linear-gradient(90deg, transparent, var(--bg-surface) 92%);
  pointer-events: none;
  z-index: 0;
}

.card-content {
  position: relative;
  z-index: 1;
  max-width: 66%;
}

.card-top {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 8px;
  flex-wrap: wrap;
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
  line-height: 1.3;
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
    min-height: unset;
  }
  .logo-stage {
    display: none;
  }
  .card-content {
    max-width: 100%;
  }

  .school {
    font-size: 1.02rem;
  }
  .degree {
    font-size: 0.86rem;
    margin-bottom: 10px;
  }
  .card-meta {
    gap: 8px;
  }
  .timeline-item {
    margin-bottom: 24px;
  }
}
</style>