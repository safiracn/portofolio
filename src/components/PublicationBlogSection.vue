<script setup>
const publications = [
  {
    title: 'Pemanfaatan Chatbot Berbasis Learning Analytics Dalam Meningkatkan Kualitas Pembelajaran Digital',
    source: 'Jurnal Profesi Insinyur Universitas Lampung',
    date: 'Dec 26, 2025',
    href: 'https://jpi.eng.unila.ac.id/index.php/ojs/article/view/264'
  }
]

const blogPosts = [
  {
    title:
      'Mahasiswa Selenggarakan Sosialisasi Moderasi Beragama: Pelajar SMAN 19 Surabaya Tanamkan Sikap Toleransi dalam Keberagaman',
    href: 'https://www.kompasiana.com/safira110306/684d2c0034777c07b279efe3/mahasiswa-selenggarakan-sosialisasi-moderasi-beragama-pelajar-sman-19-surabaya-tanamkan-sikap-toleransi-di-tengah-keberagaman'
  },
  {
    title:
      'Peran Strategis Generasi Muda dalam Membangun Indonesia Tanpa Korupsi sebagai Wujud Bela Negara',
    href: 'https://www.kompasiana.com/safira110306/692d242d34777c56944f5d52/peran-strategis-generasi-muda-dalam-membangun-indonesia-tanpa-korupsi-sebagai-wujud-bela-negara'
  }
]
</script>

<template>
  <section id="publication" class="section pub-blog">
    <div class="section-inner">
      <p class="eyebrow">Publication &amp; Blog</p>
      <h2 class="section-title">Writing &amp; research</h2>

      <!-- Publication -->
      <div class="sub-group">
        <h3 class="sub-title">Publication</h3>
        <div class="pub-list">
          <a
            v-for="p in publications"
            :key="p.href"
            class="pub-card"
            :href="p.href"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="pub-tag">Journal Article</span>
            <h4 class="pub-title">{{ p.title }}</h4>
            <div class="pub-meta">
              <span>{{ p.source }}</span>
              <span class="dot">·</span>
              <span>{{ p.date }}</span>
            </div>
            <span class="pub-arrow">Read article ↗</span>
          </a>
        </div>
      </div>

      <!-- Blog -->
      <div class="sub-group">
        <h3 class="sub-title">Blog</h3>
        <div class="blog-list">
          <a
            v-for="b in blogPosts"
            :key="b.href"
            class="blog-card"
            :href="b.href"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="pub-tag">Kompasiana</span>
            <h4 class="blog-title">{{ b.title }}</h4>
            <span class="pub-arrow">Read post ↗</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.sub-group {
  margin-bottom: 44px;
}

.sub-group:last-child {
  margin-bottom: 0;
}

.sub-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 18px;
  padding-left: 14px;
  border-left: 2px solid var(--blue-accent);
}

.pub-list,
.blog-list {
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.pub-card,
.blog-card {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
  padding: 24px 28px;
  border-radius: var(--radius-md);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.pub-card:hover,
.blog-card:hover {
  transform: translateY(-3px);
  border-color: var(--border-strong);
  background: var(--bg-elevated);
}

.pub-tag {
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  padding: 4px 12px;
  border-radius: 999px;
  background: var(--bg-elevated-2);
  color: var(--blue-accent-soft);
}

.pub-title,
.blog-title {
  font-size: 1.02rem;
  font-weight: 600;
  color: var(--text-primary);
  line-height: 1.5;
}

.pub-meta {
  font-size: 0.82rem;
  color: var(--text-secondary);
  display: flex;
  gap: 8px;
}

.dot {
  color: var(--text-muted);
}

.pub-arrow {
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--blue-accent-soft);
}
</style>