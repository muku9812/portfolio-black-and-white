<template>
  <section id="blog" class="section fade-up">
    <span class="section-label">// 08 — Blog</span>
    <h2 class="section-title">Latest Scientific Insights</h2>

    <div class="blog-grid">
      <a
          v-for="post in posts"
          :key="post.title"
          :href="post.url"
          target="_blank"
          class="card blog-card"
      >
        <div class="blog-img-wrap">
          <div class="blog-img-placeholder">
            <span>{{ post.icon }}</span>
          </div>
        </div>
        <div class="blog-body">
          <div class="blog-meta">
            <span class="blog-date">{{ post.date }}</span>
            <span class="blog-cat">{{ post.category }}</span>
          </div>
          <h4 class="blog-title">{{ post.title }}</h4>
          <p class="blog-desc">{{ post.desc }}</p>
          <span class="blog-read">Read Insight →</span>
        </div>
      </a>
    </div>
  </section>
</template>

<script setup>
const posts = [
  {
    date: 'Nov 2024',
    category: 'AI & NLP',
    icon: '🧠',
    title: 'Integrating LLM and RAG for Nepali Datasets',
    desc: 'Deep dive into the architecture and optimisation strategies for building context-aware AI systems in low-resource linguistic environments.',
    url: 'https://aastechblog.blogspot.com/2024/11/integration-of-large-language-models.html',
  },
]
</script>

<style scoped>
.section { padding: 2.5rem 0; }

.blog-grid { display: flex; flex-direction: column; gap: 1rem; }

.blog-card {
  display: flex;
  gap: 1.2rem;
  text-decoration: none;
  transition: border-color 0.25s, transform 0.2s;
}
.blog-card:hover { border-color: var(--teal-glow); transform: translateX(4px); }

.blog-img-wrap { flex-shrink: 0; }
.blog-img-placeholder {
  width: 72px;
  height: 72px;
  border-radius: var(--radius);
  background: var(--teal-dim);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.8rem;
}

.blog-body { display: flex; flex-direction: column; gap: 0.3rem; }

.blog-meta { display: flex; align-items: center; gap: 0.6rem; }
.blog-date {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-3);
}
.blog-cat {
  font-family: var(--font-mono);
  font-size: 10px;
  padding: 2px 8px;
  border-radius: 99px;
  background: var(--teal-dim);
  color: var(--teal);
  border: 1px solid var(--teal-glow);
}

.blog-title {
  font-family: var(--font-head);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-1);
  line-height: 1.35;
}
.blog-desc { font-size: 13px; color: var(--text-2); line-height: 1.6; }
.blog-read {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--teal);
  margin-top: 0.2rem;
}
</style>