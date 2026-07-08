<script setup>
import { ref, computed } from 'vue'
import emailjs from '@emailjs/browser'
import AppIcon from './AppIcon.vue'

// ⚠️ Ambil 3 nilai ini dari dashboard EmailJS kamu:
// - Service ID   → menu "Email Services" (format: service_xxxxxxx)
// - Template ID  → menu "Email Templates" (format: template_xxxxxxx)
// - Public Key   → menu "Account" > "General"
// Pastikan juga di Email Templates > Settings, field "To Email" sudah diisi
// firafizua@gmail.com (atau {{to_email}} kalau mau pakai variabel di bawah).
const EMAILJS_SERVICE_ID = 'service_anqcjy9'
const EMAILJS_TEMPLATE_ID = 'template_gjhp94l'
const EMAILJS_PUBLIC_KEY = 'LTd367Ms-MOgbLaiR'

const whatsappNumber = '6285859249749'
const emailAddress = 'firafizua@gmail.com'
const address =
  'Jl. Raya Wonoayu, Dsn. Pager RT. 03, RW. 01, Ds. Pagerngumbuk, Kec. Wonoayu, Kab. Sidoarjo, Jawa Timur 61261'
const mapsLink = 'https://maps.app.goo.gl/d75981oLqx8ihr2RA?g_st=ic'

const mapEmbedSrc =
  'https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d3956.355853725231!2d112.6156500745484!3d-7.425813673148017!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zN8KwMjUnMzMuMCJTIDExMsKwMzcnMDUuNiJF!5e0!3m2!1sid!2sid!4v1783490133446!5m2!1sid!2sid'

const form = ref({ name: '', email: '', subject: '', message: '' })
const status = ref('idle')
const errorMessage = ref('')

function scrollToForm() {
  const el = document.getElementById('contact-form')
  if (el) el.scrollIntoView({ behavior: 'smooth', block: 'center' })
}

async function sendMessage() {
  if (!form.value.name || !form.value.email || !form.value.message) {
    status.value = 'error'
    errorMessage.value = 'Please fill in your name, email, and message.'
    return
  }

  status.value = 'sending'
  errorMessage.value = ''

  try {
    await emailjs.send(
      EMAILJS_SERVICE_ID,
      EMAILJS_TEMPLATE_ID,
      {
        from_name: form.value.name,
        from_email: form.value.email,
        subject: form.value.subject || '(No subject)',
        message: form.value.message,
        to_email: emailAddress
      },
      { publicKey: EMAILJS_PUBLIC_KEY }
    )
    status.value = 'success'
    form.value = { name: '', email: '', subject: '', message: '' }
  } catch (err) {
    console.error('EmailJS error:', err)
    status.value = 'error'
    errorMessage.value = err?.text || 'Something went wrong while sending. Please try again.'
  }
}
</script>

<template>
  <section id="contact" class="section contact">
    <div class="section-inner">
      <p class="eyebrow">Contact</p>
      <h2 class="section-title">Get In Touch</h2>

      <div class="contact-grid">
        <!-- LEFT: info -->
        <div class="contact-info">
          <p class="info-lead">
            Have a project, internship opportunity, or just want to say hi?
            Reach out through WhatsApp, or send a message directly using the form.
          </p>

          <a
            class="contact-card"
            :href="`https://wa.me/${whatsappNumber}`"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="icon-chip chip-whatsapp"><AppIcon brand="whatsapp" :size="20" /></span>
            <span class="card-text">
              <span class="card-value">+62 858-5924-9749</span>
            </span>
          </a>

          <a class="contact-card" href="#contact-form" @click.prevent="scrollToForm">
            <span class="icon-chip chip-email"><AppIcon brand="gmail" :size="20" /></span>
            <span class="card-text">
              <span class="card-value">{{ emailAddress }}</span>
            </span>
          </a>

          <div class="map-block">
            <div class="map-block-head">
              <span class="icon-chip chip-location"><AppIcon name="mappin" :size="20" /></span>
              <span class="card-text">
                <span class="card-value address">{{ address }}</span>
              </span>
            </div>

            <div class="map-embed">
              <iframe
                :src="mapEmbedSrc"
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                allowfullscreen
              ></iframe>
            </div>
          </div>
        </div>

        <!-- RIGHT: form -->
        <form id="contact-form" class="contact-form" @submit.prevent="sendMessage">
          <div class="form-row">
            <div class="form-group">
              <label for="name">Your Name</label>
              <input id="name" v-model="form.name" type="text" placeholder="Safira Nisa" required />
            </div>
            <div class="form-group">
              <label for="email">Your Email</label>
              <input id="email" v-model="form.email" type="email" placeholder="safira@gmail.com" required />
            </div>
          </div>

          <div class="form-group">
            <label for="subject">Subject</label>
            <input id="subject" v-model="form.subject" type="text" placeholder="Let's collaborate" />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              v-model="form.message"
              rows="5"
              placeholder="Write your message here..."
              required
            ></textarea>
          </div>

          <button class="btn-send" type="submit" :disabled="status === 'sending'">
            {{ status === 'sending' ? 'Sending...' : 'Send Message' }}
          </button>

          <p v-if="status === 'success'" class="form-status success">
            Message sent! I'll get back to you soon.
          </p>
          <p v-if="status === 'error'" class="form-status error">
            {{ errorMessage || 'Something went wrong. Please fill all required fields or try again.' }}
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-grid {
  display: grid;
  grid-template-columns: 0.85fr 1.15fr;
  gap: 48px;
  align-items: start;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.info-lead {
  font-size: 0.96rem;
  line-height: 1.8;
  color: var(--text-secondary);
  margin-bottom: 8px;
}

.contact-card {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 18px 22px;
  border-radius: var(--radius-md);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.contact-card:hover {
  transform: translateY(-3px);
  border-color: var(--blue-accent);
  background: var(--bg-elevated);
}

.icon-chip {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 42px;
  height: 42px;
  border-radius: 12px;
  color: #fff;
  flex-shrink: 0;
}

.chip-whatsapp { background: #25d366; }
.chip-email { background: #f5f7fb; }
.chip-location { background: #e63946; }

.card-text {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.card-label {
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--blue-accent-soft);
}

.card-value {
  font-size: 0.92rem;
  font-weight: 500;
  color: var(--text-primary);
}

.card-value.address {
  font-size: 0.8rem;
  font-weight: 400;
  color: var(--text-secondary);
  line-height: 1.5;
}

.map-block {
  padding: 18px 22px;
  border-radius: var(--radius-md);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
}

.map-block-head {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 16px;
}

.map-embed {
  border-radius: var(--radius-sm);
  overflow: hidden;
  border: 1px solid var(--border-subtle);
}

.map-embed iframe {
  width: 100%;
  height: 200px;
  border: 0;
  display: block;
  filter: grayscale(0.15) contrast(1.05);
}

.map-open-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  margin-top: 12px;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--blue-accent-soft);
}

.map-open-link:hover {
  text-decoration: underline;
}

/* RIGHT: form */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 36px;
  border-radius: var(--radius-lg);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-group label {
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--text-secondary);
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px 16px;
  border-radius: var(--radius-sm);
  border: 1px solid var(--border-subtle);
  background: var(--bg-deep);
  color: var(--text-primary);
  font-family: 'Poppins', sans-serif;
  font-size: 0.9rem;
  resize: vertical;
  transition: border-color 0.2s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--blue-accent);
}

.btn-send {
  align-self: flex-start;
  padding: 13px 32px;
  border-radius: 999px;
  border: none;
  background: var(--blue-accent);
  color: #06101f;
  font-family: inherit;
  font-size: 0.92rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

.btn-send:hover:not(:disabled) {
  background: var(--blue-accent-soft);
  transform: translateY(-2px);
}

.btn-send:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.form-status {
  font-size: 0.85rem;
  font-weight: 500;
}

.form-status.success { color: #6ee7a0; }
.form-status.error { color: #f18c8c; }

@media (max-width: 860px) {
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 36px;
  }
}

@media (max-width: 560px) {
  .form-row {
    grid-template-columns: 1fr;
  }
  .contact-form {
    padding: 26px;
  }
}
</style>