# Safira Choirun Nisa' — Personal Portfolio

A single-page personal portfolio website showcasing my background as an Information Systems student, with a focus on data analytics and fullstack development.

**Live site:** [portofoliosafira.vercel.app](https://portofoliosafira.vercel.app)

![Vue](https://img.shields.io/badge/Vue-3-42b883?logo=vue.js&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?logo=vite&logoColor=white)
![Deployed on Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-000000?logo=vercel&logoColor=white)

---

## About

This portfolio is built as a single, continuously scrollable page. The navigation bar automatically highlights the section currently in view, giving visitors a clear sense of where they are without needing to click through multiple pages. It covers my education, technical and soft skills, projects, publications, organizational experience, and a working contact form.

## Sections

| Section | Description |
|---|---|
| **Home** | Introduction, quick links to download my CV and jump to the About section |
| **About** | A short summary of who I am, with links to my social profiles |
| **Education** | Academic background presented as a timeline |
| **Skills** | Soft skills, hard skills, and languages |
| **Projects** | A collection of projects with descriptions, tools used, and links to source/design files |
| **Publication & Blog** | Published research and articles |
| **Organization & Committee** | Organizational roles and event committee experience |
| **Contact** | Contact details, an embedded map, and a working message form |

## Tech Stack

- **[Vue 3](https://vuejs.org/)** — Composition API with `<script setup>`
- **[Vite](https://vitejs.dev/)** — build tool and dev server
- **[EmailJS](https://www.emailjs.com/)** — sends messages from the contact form directly to my email, with no backend required
- **[Devicon](https://devicon.dev/) & [Iconify (Logos collection)](https://icon-sets.iconify.design/logos/)** — official brand logos used throughout the site
- **[Lucide](https://lucide.dev/)** — outline icons for UI elements
- Plain CSS with custom properties (design tokens) for a consistent dark, blue-toned theme
- No database — all content is defined directly within the Vue components

## Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) 18 or later
- npm

### Installation

```bash
git clone https://github.com/safiracn/<repo-name>.git
cd <repo-name>
npm install
```

### Run locally

```bash
npm run dev
```

The site will be available at `http://localhost:5173`.

### Build for production

```bash
npm run build
```

The optimized output will be generated in the `dist/` folder.

## Deployment

This project is deployed on [Vercel](https://vercel.com/). Vercel automatically detects the Vite configuration, using `npm run build` as the build command and `dist` as the output directory. Any push to the main branch triggers a new deployment.

## Project Structure
