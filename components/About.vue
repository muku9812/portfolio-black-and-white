<template>
  <section id="research" class="section fade-up">
    <span class="section-label">// 02 — Research</span>
    <h2 class="section-title">Research Contributions</h2>

    <div
        v-for="paper in papers"
        :key="paper.title"
        class="card paper-card"
    >
      <div class="paper-meta">
        <span class="conf-badge">{{ paper.conf }}</span>
        <span class="paper-year">{{ paper.year }}</span>
        <span class="paper-role">{{ paper.role }}</span>
      </div>
      <h3 class="paper-title">{{ paper.title }}</h3>
      <p class="paper-desc">{{ paper.desc }}</p>
      <div class="paper-status" :class="paper.statusClass">
        <span class="status-dot" />{{ paper.status }}
      </div>
      <div style="margin-top:1rem">
        <span v-for="t in paper.tags" :key="t" class="tag">{{ t }}</span>
      </div>
    </div>
  </section>
</template>

<script setup>
const papers = [
  {
    conf: 'IEEE ICTP 2026',
    year: '2026',
    role: 'Main Author & Presenter',
    title: 'Analyzing Conversational LLMs for Nepali Municipal Services: A Comparative Study of Retrieval-Augmented and Fine-Tuned Approaches',
    desc: 'Presented at the IEEE International Conference on ICT and Photonics (ICTP 2026). Investigates the efficacy of Generative AI within low-resource linguistic frameworks, providing a foundational framework for deploying scalable AI solutions in the public sector. Conducts a rigorous comparative assessment between RAG and Supervised Fine-tuning (SFT), analysing response fidelity, contextual grounding, and computational feasibility for Nepali Municipal Service delivery.',
    status: 'Publication: Forthcoming',
    statusClass: 'status-amber',
    tags: ['RAG', 'LLMs', 'NLP', 'Low-Resource Languages', 'Nepali', 'SFT', 'Municipal AI'],
  },
]
</script>

<style scoped>
.section { padding: 2.5rem 0; }

.paper-card { margin-bottom: 1.2rem; }

.paper-meta {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 0.75rem;
}
.conf-badge {
  font-family: var(--font-mono);
  font-size: 10px;
  padding: 3px 10px;
  border-radius: 99px;
  background: var(--teal-dim);
  border: 1px solid var(--teal-glow);
  color: var(--teal);
  font-weight: 500;
  letter-spacing: 0.05em;
}
.paper-year {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-3);
}
.paper-role {
  font-family: var(--font-mono);
  font-size: 10px;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--amber);
  margin-left: auto;
}

.paper-title {
  font-family: var(--font-head);
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-1);
  line-height: 1.4;
  margin-bottom: 0.6rem;
}
.paper-desc {
  font-size: 13.5px;
  color: var(--text-2);
  line-height: 1.7;
}

.paper-status {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-family: var(--font-mono);
  font-size: 11px;
  margin-top: 0.9rem;
}
.status-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: currentColor;
  animation: pulse 2s ease infinite;
}
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.35; }
}
.status-amber { color: var(--amber); }
.status-green  { color: var(--teal); }
</style>