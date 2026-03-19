<template>
  <section id="about" class="section fade-up">
    <span class="section-label">// 01 — About</span>
    <h2 class="section-title">Aastha Paudel</h2>

    <p class="bio">
      Dedicated <strong>AI &amp; Machine Learning Researcher</strong> specialising in
      <em>Natural Language Processing</em> and <em>Data Science</em>. Focused on enhancing
      Retrieval-Augmented Generation (RAG) pipelines and Large Language Models to drive
      scholarly and industrial innovation — with a particular emphasis on
      <strong>low-resource languages</strong> such as Nepali.
    </p>
    <p class="bio" style="margin-top:0.8rem">
      Computer Engineering graduate from <strong>IOE, Tribhuvan University</strong>.
      Currently a Laravel Developer at <strong>Trilokya Technology</strong> while
      continuing active research. Microsoft Learn Student Ambassador and Vice Project Lead
      at Code For Change, Pokhara.
    </p>

    <div class="divider" />

    <!-- Research Interests -->
    <div class="interests">
      <h3 class="sub-heading">Research Interests</h3>
      <div class="tags-row">
        <span v-for="t in interests" :key="t" class="tag">{{ t }}</span>
      </div>
    </div>

    <div class="divider" />

    <!-- Quick links row -->
    <div class="quick-links">
      <a v-for="l in links" :key="l.label" :href="l.href" target="_blank" class="ql">
        <span class="ql-icon">{{ l.icon }}</span>{{ l.label }}
      </a>
    </div>
  </section>
</template>

<script setup>
const interests = [
  'Large Language Models',
  'Retrieval-Augmented Generation',
  'Natural Language Processing',
  'Low-Resource NLP',
  'Data Science',
  'Comparative AI Evaluation',
  'Multilingual AI Systems',
]

const links = [
  { label: 'Google Scholar', href: 'https://scholar.google.com/citations?user=lYSo4aUAAAAJ', icon: '◈' },
  { label: 'GitHub',         href: 'https://github.com/Aasthapaudel',                         icon: '⌥' },
  { label: 'LinkedIn',       href: 'https://www.linkedin.com/in/aastha-paudel-1b3b001b9/',    icon: '↗' },
  { label: 'Email',          href: 'mailto:aasthapdl121@gmail.com',                            icon: '✉' },
  { label: 'Blog',           href: 'https://aastechblog.blogspot.com',                         icon: '✍' },
]
</script>

<style scoped>
.section { padding: 3rem 0 2rem; }
.bio { color: var(--text-2); max-width: 100%; }
.bio strong { color: var(--text-1); font-weight: 500; }
.bio em { color: var(--teal); font-style: normal; }

.sub-heading {
  font-family: var(--font-mono);
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--text-3);
  margin-bottom: 0.7rem;
}

.interests { }
.tags-row { display: flex; flex-wrap: wrap; gap: 4px; }

.quick-links {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}
.ql {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-family: var(--font-mono);
  font-size: 12px;
  padding: 6px 14px;
  border-radius: var(--radius);
  border: 1px solid var(--border);
  color: var(--text-2);
  transition: border-color 0.2s, color 0.2s;
}
.ql:hover { border-color: var(--teal-glow); color: var(--teal); }
.ql-icon { font-size: 13px; color: var(--teal); }
</style>