<script setup>
const projects = [
  {
    title: 'Website Ruang Karya MAN 1 Gresik',
    description:
      'Built a web-based marketplace platform for promoting and selling student-produced furniture, fashion products, and handicrafts, with dedicated features for customers and administrators.',
    tools: ['Laravel', 'MVC', 'MySQL'],
    image: '/images/ruangkarya.jpeg',
    links: [
      { label: 'GitHub', href: 'https://github.com/safiracn/Website-Ruang-Karya-MAN-1-Gresik---Kelompok-4---Kelas-IV-B.git' }
    ]
  },
  {
    title: 'MONY - UI/UX Design',
    description:
      'Created UI/UX designs for a pawn-based savings and loan cooperative application, focusing on intuitive workflows for both members and administrators.',
    tools: ['Figma'],
    image: '/images/monyuiux.png',
    links: [
      { label: 'Figma', href: 'https://www.figma.com/design/iRhuO0qTkJZssR2fLd7Sut/PEMMOB?node-id=1018-263&t=DfcPkgTPqBAhr0uI-1' }
    ]
  },
  {
    title: 'MONY - Savings & Loan Cooperative App',
    description:
      'Developed a mobile application for a pawn-based savings and loan cooperative, enabling members to access financial services and administrators to manage cooperative operations through a structured MVVM architecture.',
    tools: ['Mobile App', 'Flutter', 'MVVM'],
    image: '/images/monymobile.png',
    links: [
      { label: 'View', href: 'https://www.mediafire.com/file/us26zx00zfbop3d/app-release.apk/file' },
      { label: 'GitHub', href: 'https://github.com/safiracn/MONY-APLIKASISIMPANPINJAMBERBASISGADAI.git' }
    ]
  },
  {
    title: 'Cloud Service Usage Impact Analysis',
    description:
      'Conducted descriptive and inferential statistical analysis using Jamovi, testing 5 methods including regression, chi-square, t-test, ANOVA, and Mann-Whitney U, then applying SEM-PLS via WarpPLS, finding a significant positive effect of cloud service usage on student academic effectiveness (path coefficient 0.534, p < 0.001, R-squared 0.29).',
    tools: ['Jamovi', 'WarpPLS'],
    image: '/images/statkom.png',
    links: [
      { label: 'Report', href: 'https://drive.google.com/file/d/1hlx-LT9E8BRIjxeDl8fSRRjFNzx2WDJv/view?usp=sharing' }
    ]
  },
  {
    title: 'LOWONG - Job Platform · UI/UX Design',
    description:
      'Designed a job marketplace platform connecting job seekers and opportunity providers in part-time, freelance, and volunteer categories through a user-friendly and accessible interface.',
    tools: ['Figma'],
    image: '/images/lowong.png',
    links: [
      { label: 'Figma', href: 'https://www.figma.com/design/XEgMmO4qARv9hECYTRGb5V/E-BUSINESS?node-id=1237-4905&t=9zxwbYUEXq30n4sD-1' }
    ]
  },
  {
    title: 'LUNARA (Lancar Usaha Rakyat) - UI/UX Design',
    description:
      'Designed a user-centered interface and user experience for a community business empowerment platform aimed at improving accessibility and usability for small business owners.',
    tools: ['Figma'],
    image: '/images/lunara.png',
    links: [
      { label: 'Figma', href: 'https://www.figma.com/design/SzKMPkJSzmgusf1rWK851N/UI-UX-Lunara_Localscape?node-id=0-1&t=XERhwXfMDUj7WYRU-1' }
    ]
  },
  {
    title: 'Lingora - Gamified Sign Language Learning App',
    description:
      'Designed an AI-powered, gamified sign language learning application for Samsung Solve for Tomorrow 2026. The platform leverages gesture recognition technology to provide real-time feedback, structured learning paths, and interactive challenges, supporting inclusive communication through accessible BISINDO and SIBI learning experiences.',
    tools: ['Design Thinking', 'UI/UX Design'],
    image: '/images/lingora.png',
    links: [
      { label: 'Figma', href: 'https://www.figma.com/design/7RDXzBiiOwW3EM9WPHJjha/SFT-TIM-RAJAWALI?node-id=0-1&t=GZ5L0F2uecI6Cp4I-1' },
      { label: 'Report', href: 'https://drive.google.com/file/d/1mDK18Z1l-GGuRiU7XLP_BbxdRmuEYL1u/view?usp=sharing' }
    ]
  },
  {
    title: 'IT Performance Measurement Dashboard - Wowrack Case Study',
    description:
      'Developed an interactive web-based KPI dashboard for measuring IT performance using Wowrack as the case study. The dashboard applies the IT Balanced Scorecard (IT BSC) framework to visualize key performance indicators across Corporate Contribution, Customer Orientation, Operational Excellence, and Future Orientation, supporting performance monitoring and strategic decision-making.',
    tools: ['Website'],
    image: '/images/pkti.jpeg',
   links: [
      { label: 'View', href: 'https://v0-dashboard-deployment-chi.vercel.app/' }
    ]
  },
  {
    title: 'Information System Project Planning – Ruang Karya MAN 1 Gresik',
    description:
      'Developed a comprehensive project management plan for the Ruang Karya MAN 1 Gresik e-commerce website. The project included project charter development, scope definition, work breakdown structure (WBS), scheduling, budgeting, risk management, resource planning, and Agile Scrum sprint planning to ensure effective project execution from initiation to deployment.',
    tools: ['Agile Scrum', 'Notion', 'Gantt Chart', 'Project Charter', 'Work Breakdown Structure (WBS)'],
    image: '/images/mpsi.png',
    links: [
      { label: 'Report', href: 'https://drive.google.com/file/d/1M0C4SWCxx9QmkhuqT84jNC1Tb4R1xyPn/view?usp=sharing' }
    ]
  },
  {
    title: 'Cinema Ticket Booking App',
    description:
      'Developed a desktop-based cinema ticket booking application that enables users to browse movie schedules, select seats, and manage ticket reservations.',
    tools: ['Java', 'MySQL'],
    image: '/images/basdat.png',
    links: [
      { label: 'GitHub', href: 'https://github.com/safiracn/Project-Basis-Data-Kel-2-II-B.git' }
    ]
  },
    {
    title: 'Personal Portfolio Website',
    description:
      'A personal portfolio website built to showcase my journey as an Information System student with a focus on data analytics and fullstack development. Designed with a clean navy, gold, and blue theme, the site presents my profile, education, skills, and a collection of more than 10 projects across web development, mobile development, UI/UX design, and statistical analysis, along with my involvement in campus organizations and committees. Built using Vue 3 and Vite with a component based structure and centralized data management, this project reflects not only my technical execution but also my attention to detail in translating personal branding into a functional, well structured digital presence.',
    tools: ['Vue', 'Vite'],
    image: '/images/portofolio.jpeg',
    links: [
      { label: 'View', href: 'https://portofoliosafira.vercel.app/' },
      { label: 'GitHub', href: 'https://github.com/safiracn/portofolio.git' }
    ]
  },
  {
    title: 'Noona Dalgona - MSME Cashier App',
    description:
      'Developed a desktop-based cashier application for an MSME to manage sales transactions, order processing, and payment recording efficiently.',
    tools: ['Desktop App', 'Visual Basic .NET'],
    image: '/images/noona.png',
    links: []
  },
]
</script>

<template>
  <section id="projects" class="section projects">
    <div class="section-inner">
      <p class="eyebrow">Projects</p>
      <h2 class="section-title">Things I've built</h2>

      <div class="projects-grid">
        <article v-for="p in projects" :key="p.title" class="project-card">
          <div class="project-image">
            <img v-if="p.image" :src="p.image" :alt="p.title" />
            <div v-else class="image-placeholder">
              <span>Project Image</span>
            </div>
          </div>

          <div class="project-body">
            <h3 class="project-title">{{ p.title }}</h3>
            <p class="project-desc">{{ p.description }}</p>

            <div class="tool-tags">
              <span v-for="t in p.tools" :key="t" class="tool-tag">{{ t }}</span>
            </div>

            <div v-if="p.links.length" class="project-links">
              <a
                v-for="l in p.links"
                :key="l.href"
                class="project-link"
                :href="l.href"
                target="_blank"
                rel="noopener noreferrer"
              >
                {{ l.label }} <span class="arrow">↗</span>
              </a>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 22px;
}

.project-card {
  display: flex;
  flex-direction: column;
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  overflow: hidden;
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.project-card:hover {
  transform: translateY(-4px);
  border-color: var(--border-strong);
}

.project-image {
  width: 100%;
  aspect-ratio: 16 / 10;
  background: var(--bg-elevated);
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: fit;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px dashed var(--border-strong);
}

.image-placeholder span {
  font-size: 0.78rem;
  color: var(--text-muted);
}

.project-body {
  padding: 22px 24px 26px;
  display: flex;
  flex-direction: column;
  flex: 1;
}

.project-title {
  font-size: 1.05rem;
  font-weight: 700;
  margin-bottom: 10px;
}

.project-desc {
  font-size: 0.86rem;
  line-height: 1.7;
  color: var(--text-secondary);
  flex: 1;
}

.tool-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 16px;
}

.tool-tag {
  font-size: 0.72rem;
  font-weight: 600;
  padding: 5px 12px;
  border-radius: 999px;
  background: var(--bg-elevated-2);
  color: var(--blue-accent-soft);
}

.project-links {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 18px;
}

.project-link {
  font-size: 0.8rem;
  font-weight: 600;
  padding: 8px 16px;
  border-radius: 999px;
  border: 1px solid var(--border-subtle);
  color: var(--text-primary);
  transition: border-color 0.2s ease, color 0.2s ease, transform 0.2s ease;
}

.project-link:hover {
  border-color: var(--blue-accent);
  color: var(--blue-accent-soft);
  transform: translateY(-2px);
}

.arrow {
  display: inline-block;
}
</style>