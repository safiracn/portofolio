<script setup>
import { ref } from 'vue'

const activeTab = ref('organisasi')

// Tiap item bisa diisi array `images` (path foto kegiatan/sertifikat).
// Kosongkan array-nya (default) kalau belum ada fotonya -> otomatis jadi placeholder.
const organisasi = [
  {
    name: 'Information System Community (ISCOM)',
    role: 'Secretary 2',
    images: []
  },
  {
    name: 'Veteran Robotic (VETRO)',
    role: 'Member',
    images: []
  },
  {
    name: 'HIMASIFO UPN "Veteran" Jawa Timur',
    role: 'Staff of Advocacy & Student Welfare Department',
    images: []
  }
]

const kepanitiaan = [
  { name: 'Aksi Belajar Program', role: 'Teaching Staff', images: [] },
  {
    name: 'GRADASI (Gabungan Rangkaian Pengkaderan Sistem Informasi) 2025',
    role: 'Event Division Member & Master of Ceremony, Pekan Serasi / Puncak Pengkaderan Sistem Informasi (PENSI) Day 1',
    images: []
  },
  {
    name: 'SICERIA (Sistem Informasi Cerdas dan Peduli Anak) 2025',
    role: 'Head of Event Division',
    images: []
  },
  {
    name: 'Forbasi (Forum Mahasiswa Baru Sistem Informasi) 2025',
    role: 'Presenter',
    images: []
  },
  {
    name: 'SITASI (Seminar Nasional dan Teknologi Sistem Informasi) Bela Negara 2025',
    role: 'Event Division Member',
    images: []
  },
  {
    name: 'Open Talk of the Information Systems Department and the Faculty of Computer Science',
    role: 'Moderator & Event Division Member',
    images: []
  },
  {
    name: 'Information Systems Dies Natalis 2025',
    role: 'Event Division Member',
    images: []
  },
  {
    name: 'Islamic Education Final Project',
    role: 'Project Leader & Presenter',
    images: []
  },
  {
    name: 'Sosialisasi Informasi dan Arahan Persiapan Skripsi (SIAPS) 2025',
    role: 'Moderator & Master of Ceremony',
    images: []
  },
  { name: 'Blood Donation Program', role: 'Event Division Member', images: [] },
  {
    name: 'Ramadhan Berbagi Bersama Sistem Informasi (RADIASI)',
    role: 'Head of Event Division',
    images: []
  },
  {
    name: 'Information Systems Department Student Election (PEMIRA)',
    role: 'Public Relations Member',
    images: []
  },
  {
    name: 'Aktif Berkarya Bersama Hima (AKSA) 2025',
    role: 'Master of Ceremony',
    images: []
  },
  {
    name: 'ISMURF (Information System Make Unity Relationship Forever)',
    role: 'Fundraising Division Member',
    images: []
  },
  { name: 'Choir — SMAN 1 Wonoayu', role: 'Member', images: [] }
]
</script>

<template>
  <section id="organization" class="section org-committee">
    <div class="section-inner">
      <p class="eyebrow">Organization &amp; Committee</p>
      <h2 class="section-title">Beyond the classroom</h2>

      <div class="tab-switch">
        <button
          class="tab-btn"
          :class="{ active: activeTab === 'organisasi' }"
          @click="activeTab = 'organisasi'"
        >
          Organization
        </button>
        <button
          class="tab-btn"
          :class="{ active: activeTab === 'kepanitiaan' }"
          @click="activeTab = 'kepanitiaan'"
        >
          Committee
        </button>
      </div>

      <div v-show="activeTab === 'organisasi'" class="card-grid">
        <article v-for="o in organisasi" :key="o.name" class="oc-card">
          <div class="photo-strip">
            <template v-if="o.images.length">
              <img
                v-for="(img, idx) in o.images.slice(0, 3)"
                :key="idx"
                :src="img"
                :alt="o.name"
              />
            </template>
            <div v-else class="photo-placeholder">
              <span>Photos / Certificate</span>
            </div>
          </div>
          <h3 class="oc-name">{{ o.name }}</h3>
          <p class="oc-role">{{ o.role }}</p>
        </article>
      </div>

      <div v-show="activeTab === 'kepanitiaan'" class="card-grid">
        <article v-for="c in kepanitiaan" :key="c.name" class="oc-card">
          <div class="photo-strip">
            <template v-if="c.images.length">
              <img
                v-for="(img, idx) in c.images.slice(0, 3)"
                :key="idx"
                :src="img"
                :alt="c.name"
              />
            </template>
            <div v-else class="photo-placeholder">
              <span>Photos / Certificate</span>
            </div>
          </div>
          <h3 class="oc-name">{{ c.name }}</h3>
          <p class="oc-role">{{ c.role }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tab-switch {
  display: inline-flex;
  gap: 4px;
  padding: 4px;
  border-radius: 999px;
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  margin-bottom: 36px;
}

.tab-btn {
  padding: 10px 24px;
  border-radius: 999px;
  font-size: 0.86rem;
  font-weight: 600;
  color: var(--text-secondary);
  background: transparent;
  border: none;
  cursor: pointer;
  transition: background 0.2s ease, color 0.2s ease;
  font-family: inherit;
}

.tab-btn.active {
  background: var(--blue-accent);
  color: #06101f;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 20px;
}

.oc-card {
  display: flex;
  flex-direction: column;
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  overflow: hidden;
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.oc-card:hover {
  transform: translateY(-3px);
  border-color: var(--border-strong);
}

.photo-strip {
  display: flex;
  gap: 2px;
  height: 120px;
  background: var(--bg-elevated);
}

.photo-strip img {
  flex: 1;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.photo-placeholder {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px dashed var(--border-strong);
}

.photo-placeholder span {
  font-size: 0.74rem;
  color: var(--text-muted);
  text-align: center;
  padding: 0 12px;
}

.oc-name {
  font-size: 0.96rem;
  font-weight: 600;
  padding: 18px 20px 4px;
  line-height: 1.4;
}

.oc-role {
  font-size: 0.82rem;
  color: var(--text-secondary);
  padding: 0 20px 20px;
}
</style>