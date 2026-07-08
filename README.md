# Safira Choirun Nisa' — Portfolio

Website portofolio 1 halaman (single-page) dibuat dengan **Vue 3 + Vite**, siap di-deploy ke **Vercel**. Tidak menggunakan database — semua konten ditulis langsung di dalam komponen Vue.

Progress saat ini: **Home, About, Education, Skills** sudah selesai. Section berikutnya (Projects, Publication & Blog, Organization & Committee, Contact) akan menyusul.

## Menjalankan secara lokal

```bash
npm install
npm run dev
```

Lalu buka `http://localhost:5173`.

## Build untuk production

```bash
npm run build
```

Hasil build ada di folder `dist/`.

## Deploy ke Vercel

1. Push project ini ke repository GitHub.
2. Buka [vercel.com](https://vercel.com) → **New Project** → import repo tersebut.
3. Vercel akan otomatis mendeteksi framework **Vite** (build command `npm run build`, output folder `dist`) — biarkan default, lalu klik **Deploy**.

Atau lewat CLI:

```bash
npm install -g vercel
vercel
```

## Mengganti konten

### 1. Foto profil (section About)
File: `src/components/AboutSection.vue`

Cari komentar `PHOTO PLACEHOLDER`, lalu ganti `<div class="photo-placeholder">...</div>` dengan tag `<img>`:

```html
<img src="/images/safira-photo.png" alt="Safira Choirun Nisa'" class="photo-img" />
```

Taruh file fotomu di `public/images/` (disarankan PNG dengan background transparan supaya menyatu dengan elemen dekorasi di belakangnya). Kamu mungkin perlu menambah sedikit CSS `.photo-img { width: 100%; height: 100%; object-fit: contain; }` di bagian `<style scoped>`.

### 2. File CV (tombol "Download CV" di Home)
File: `src/components/HomeSection.vue`

Taruh file CV (PDF) di `public/cv/`, lalu sesuaikan `href` pada tombol Download CV, contoh:

```html
<a class="btn btn-primary" href="/cv/Safira-Choirun-Nisa-CV.pdf" download>
```

### 3. Menambah section baru (Projects, Publication & Blog, dst.)
File: `src/App.vue`

1. Tambahkan entri baru ke array `navSections`, misalnya `{ id: 'projects', label: 'Projects' }`.
2. Buat komponen baru di `src/components/`, misalnya `ProjectsSection.vue`, dengan root elemen `<section id="projects" class="section">`.
3. Import dan pasang komponennya di dalam `<main>` pada `App.vue`, sesuai urutan pada `navSections`.

Nav bar akan otomatis mendeteksi section yang sedang aktif saat di-scroll (via `IntersectionObserver`), tidak perlu diubah manual.

## Struktur folder

```
src/
  components/
    NavBar.vue
    HomeSection.vue
    AboutSection.vue
    EducationSection.vue
    SkillsSection.vue
  App.vue        -> merangkai semua section + logic scrollspy
  main.js
  style.css      -> design tokens (warna, spacing) & style global
public/
  cv/            -> taruh file CV di sini
  images/        -> taruh foto profil di sini
```

## Desain

- Palet warna: biru dominan gelap (`--bg-deep`, `--bg-surface`, `--blue-accent`, dst. — lihat `src/style.css`).
- Font: Poppins (dimuat dari Google Fonts di `index.html`).
- Semua elemen berbasis teks (tanpa ikon/logo) sesuai permintaan — lebih ringan dan sederhana.
