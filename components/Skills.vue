<template>
  <section id="skills" class="section fade-up">
    <span class="section-label">// 04 — Skills</span>
    <h2 class="section-title">Technical &amp; Professional Skills</h2>

    <div class="skills-list">
      <div v-for="group in skillGroups" :key="group.field" class="skill-row">
        <div class="row-left">
          <div class="skill-field">{{ group.field }}</div>
          <h4 class="skill-group-title">{{ group.title }}</h4>
        </div>
        <div class="row-right">
          <div class="skill-tags">
            <span v-for="s in group.skills" :key="s" class="tag">{{ s }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skillGroups = [
  {
    field: 'Scientific Inquiry',
    title: 'Research & Data Science',
    skills: ['Methodology', 'Academic Writing', 'Statistics', 'Data Analysis', 'Data Science', 'Data Visualisation', 'Experimental Design'],
  },
  {
    field: 'Computational Intelligence',
    title: 'AI & Machine Learning',
    skills: ['LLMs & RAG', 'NLP', 'PyTorch', 'Scikit-learn', 'Machine Learning', 'Hugging Face'],
  },
  {
    field: 'Industrial Engineering',
    title: 'Software & Industrial Frameworks',
    skills: ['Laravel (PHP)', 'Livewire', 'Python (Flask)', 'C++', 'Backend Architecture', 'API Design', 'Docker', 'RESTful APIs', 'Database Design'],
  },
  {
    field: 'Infrastructure & Methodology',
    title: 'Systems & Research Tools',
    skills: ['Git & GitHub', 'Docker & Linux', 'DSA', 'Scientific Computing', 'Project Mgmt', 'Technical Communication'],
  },
  {
    field: 'Data & Analytics',
    title: 'Data Tools',
    skills: ['Microsoft Excel', 'Google Sheets', 'SQL', 'Pandas', 'NumPy', 'Power BI', 'Matplotlib'],
  },
]
</script>

<style scoped>
.section { padding: 2.5rem 0; }

.skills-list {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.skill-row {
  display: grid;
  grid-template-columns: 220px 1fr;
  gap: 1.5rem;
  align-items: center;
  padding: 1.1rem 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.2s, padding 0.2s;
}
.skill-row:first-child { border-top: 1px solid var(--border); }
.skill-row:last-child  { border-bottom: none; }

.skill-row:hover {
  background: var(--teal-dim);
  border-radius: var(--radius);
  padding-left: 0.6rem;
  padding-right: 0.6rem;
}

.row-left {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}

.row-right {
  display: flex;
  align-items: center;
}

.skill-field {
  font-family: var(--font-mono);
  font-size: 10px;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--teal);
}

.skill-group-title {
  font-family: var(--font-head);
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--text-1);
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
}

@media (max-width: 768px) {
  .skill-row {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }
}
</style>