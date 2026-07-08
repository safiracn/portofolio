<script setup>
import { ref } from 'vue'
import emailjs from '@emailjs/browser'

// ⚠️ Ambil 3 nilai ini dari dashboard EmailJS kamu:
// - Service ID   → menu "Email Services" (format: service_xxxxxxx)
// - Template ID  → menu "Email Templates" (format: template_xxxxxxx)
// - Public Key   → menu "Account" > "General"
// Pastikan juga di Email Templates > Settings, field "To Email" sudah diisi
// firafizua@gmail.com (atau {{to_email}} kalau mau pakai variabel di bawah).
const EMAILJS_SERVICE_ID = 'service_anqcjy9'
const EMAILJS_TEMPLATE_ID = 'template_gjhp94l'
const EMAILJS_PUBLIC_KEY = 'LTd367Ms-MOgbLaiR'

const whatsappNumber = '6285859249749' // format internasional, tanpa "+"
const emailAddress = 'firafizua@gmail.com'
const address =
  'Jl. Raya Wonoayu, Dsn. Pager RT. 03, RW. 01, Ds. Pagerngumbuk, Kec. Wonoayu, Kab. Sidoarjo, Jawa Timur 61261'
const mapsLink = 'https://maps.app.goo.gl/d75981oLqx8ihr2RA?g_st=ic'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const status = ref('idle') // idle | sending | success | error
const errorMessage = ref('')

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
    errorMessage.value =
      err?.text || 'Something went wrong while sending. Please try again.'
  }
}
</script>

<template>
  <section id="contact" class="section contact">
    <div class="section-inner">
      <p class="eyebrow">Contact</p>
      <h2 class="section-title">Get In Touch</h2>

      <div class="contact-grid">
        <!-- LEFT: contact info -->
        <div class="contact-info">
          <p class="info-lead">
            Have a project, internship opportunity, or just want to say hi?
            Reach out through any of the channels below, or send a message
            directly using the form.
          </p>

          <div class="info-cards">
            <a
              class="contact-card"
              :href="`https://wa.me/${whatsappNumber}`"
              target="_blank"
              rel="noopener noreferrer"
            >
              <span class="card-label">WhatsApp</span>
              <span class="card-value">+62 858-5924-9749</span>
            </a>

            <a class="contact-card" :href="`mailto:${emailAddress}`">
              <span class="card-label">Email</span>
              <span class="card-value">{{ emailAddress }}</span>
            </a>

            <a
              class="contact-card"
              :href="mapsLink"
              target="_blank"
              rel="noopener noreferrer"
            >
              <span class="card-label">Location</span>
              <span class="card-value address">{{ address }}</span>
            </a>
          </div>
        </div>

        <!-- RIGHT: form -->
        <form class="contact-form" @submit.prevent="sendMessage">
          <div class="form-row">
            <div class="form-group">
              <label for="name">Your Name</label>
              <input id="name" v-model="form.name" type="text" placeholder="Safira Nisa" required />
            </div>
            <div class="form-group">
              <label for="email">Your Email</label>
              <input id="email" v-model="form.email" type="email" placeholder="safira@email.com" required />
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

/* LEFT column */
.contact-info {
  display: flex;
  flex-direction: column;
  gap: 28px;
}

.info-lead {
  font-size: 0.96rem;
  line-height: 1.8;
  color: var(--text-secondary);
}

.info-cards {
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.contact-card {
  display: flex;
  flex-direction: column;
  gap: 6px;
  padding: 20px 24px;
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

.card-label {
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--blue-accent-soft);
}

.card-value {
  font-size: 0.94rem;
  font-weight: 500;
  color: var(--text-primary);
}

.card-value.address {
  font-size: 0.82rem;
  font-weight: 400;
  color: var(--text-secondary);
  line-height: 1.5;
}

/* RIGHT column: form */
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

.form-status.success {
  color: #6ee7a0;
}

.form-status.error {
  color: #f18c8c;
}

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