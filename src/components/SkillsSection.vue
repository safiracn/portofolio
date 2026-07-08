<script setup>
const softSkills = [
  'Public Speaking',
  'Communication',
  'Teamwork',
  'Leadership',
  'Problem Solving',
  'Critical Thinking'
]

const hardSkills = [
  'Java',
  'Visual Basic',
  'SQL',
  'HTML',
  'CSS',
  'JavaScript',
  'Jamovi',
  'Microsoft Office',
  'Git',
  'GitHub',
  'Visual Studio Code',
  'Figma'
]

const languages = [
  { name: 'Indonesian', level: 'Native' },
  { name: 'English', level: 'Basic' }
]
</script>

<template>
  <section id="skills" class="section skills">
    <div class="section-inner">
      <p class="eyebrow">Skills</p>
      <h2 class="section-title">What I bring to the table</h2>

      <div class="skill-group">
        <h3 class="group-title">Soft Skills</h3>
        <div class="tag-cloud">
          <span v-for="s in softSkills" :key="s" class="tag">{{ s }}</span>
        </div>
      </div>

      <div class="skill-group">
        <h3 class="group-title">Hard Skills</h3>
        <div class="tag-cloud">
          <span v-for="s in hardSkills" :key="s" class="tag tag-accent">{{ s }}</span>
        </div>
      </div>

      <div class="skill-group">
        <h3 class="group-title">Languages</h3>
        <div class="lang-row">
          <div v-for="l in languages" :key="l.name" class="lang-card">
            <span class="lang-name">{{ l.name }}</span>
            <span class="lang-level">{{ l.level }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skill-group {
  margin-bottom: 40px;
}

.skill-group:last-child {
  margin-bottom: 0;
}

.group-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 18px;
  padding-left: 14px;
  border-left: 2px solid var(--blue-accent);
}

.tag-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.tag {
  font-size: 0.85rem;
  font-weight: 500;
  padding: 9px 18px;
  border-radius: 999px;
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
  color: var(--text-secondary);
  transition: transform 0.2s ease, border-color 0.2s ease, color 0.2s ease;
}

.tag:hover {
  transform: translateY(-2px);
  border-color: var(--border-strong);
  color: var(--text-primary);
}

.tag-accent {
  color: var(--blue-accent-soft);
  background: rgba(76, 126, 255, 0.08);
}

.tag-accent:hover {
  border-color: var(--blue-accent);
}

.lang-row {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}

.lang-card {
  display: flex;
  flex-direction: column;
  gap: 4px;
  min-width: 160px;
  padding: 16px 22px;
  border-radius: var(--radius-md);
  background: var(--bg-surface);
  border: 1px solid var(--border-subtle);
}

.lang-name {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
}

.lang-level {
  font-size: 0.78rem;
  color: var(--blue-accent-soft);
  font-weight: 500;
}
</style>
