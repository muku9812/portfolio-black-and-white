<template>
  <section id="projects" class="section fade-up">
    <span class="section-label">// 03 — Projects</span>
    <h2 class="section-title">Research Engineering &amp; Applied AI</h2>

    <!-- Industrial -->
    <h3 class="group-heading">
      <span class="group-line" />
      Industrial Experience
      <span class="group-line" />
    </h3>
    <div class="projects-list">
      <div v-for="p in industrial" :key="p.title" class="project-row">
        <div class="row-left">
          <span class="project-type">{{ p.type }}</span>
          <h4 class="project-title">{{ p.title }}</h4>
        </div>
        <div class="row-right">
          <p class="project-desc">{{ p.desc }}</p>
          <div class="project-tags">
            <span v-for="t in p.tags" :key="t" class="tag">{{ t }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Academic -->
    <h3 class="group-heading" style="margin-top:2.5rem">
      <span class="group-line" />
      Academic Research &amp; Prototypes
      <span class="group-line" />
    </h3>

    <!-- Featured row -->
    <div class="featured-row">
      <div class="row-left">
        <span class="feat-label">★ Featured</span>
        <h4 class="project-title large">NagarGPT — LLM-Based Multilingual Voice Chatbot</h4>
      </div>
      <div class="row-right">
        <p class="project-desc">
          A domain-adaptive AI chatbot with multilingual text-voice I/O, delivering contextual
          responses via an LLM + RAG pipeline. Scaled for real-world accessibility with RESTful
          API deployment using Ngrok.
        </p>
        <div class="project-tags">
          <span v-for="t in nagarTags" :key="t" class="tag">{{ t }}</span>
        </div>
      </div>
    </div>

    <div class="projects-list">
      <div v-for="p in academic" :key="p.title" class="project-row">
        <div class="row-left">
          <span class="project-type">{{ p.type }}</span>
          <h4 class="project-title">{{ p.title }}</h4>
        </div>
        <div class="row-right">
          <p class="project-desc">{{ p.desc }}</p>
          <div class="project-tags">
            <span v-for="t in p.tags" :key="t" class="tag">{{ t }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const industrial = [
  {
    type: 'LMS & Education Tech',
    title: 'EduPath — Learning Management System',
    desc: 'Scalable Knowledge Delivery Architecture for structured digital education. Zoom-integrated pedagogical workflows with secure PDF-based content distribution.',
    tags: ['System Architecture', 'Knowledge Delivery', 'API Ecosystems', 'Laravel'],
  },
  {
    type: 'Multi-Service Platform',
    title: 'KaamSansar — Ecosystem Modelling',
    desc: 'Comprehensive digital ecosystem for multi-service discovery including job matching and predictive horoscope analysis. Modular architecture for secure multi-tenant environments.',
    tags: ['Ecosystem Modelling', 'Modular Frameworks', 'Discovery Engines'],
  },
  {
    type: 'Governance & Compliance',
    title: 'GRC Management System',
    desc: 'Enterprise-grade platform incorporating Audit Management, Asset Management, and Compliance Tracking with risk assessment workflows and real-time dashboards.',
    tags: ['Audit Lifecycle', 'Risk Assessment', 'Reporting', 'Laravel'],
  },
  {
    type: 'ITAM & Service Mgmt',
    title: 'TechAsset Management System',
    desc: 'Technology asset management solution with automated asset discovery (FQDN/IP-based), centralised inventory, and integrated ticket management for improved IT visibility.',
    tags: ['Automated Discovery', 'Lifecycle Tracking', 'Service Management'],
  },
  {
    type: 'Certification Tech',
    title: 'Certificate Management System',
    desc: 'Automated system for issuing, tracking, and verifying professional certifications with secure verification workflows, automated PDF generation, and RBAC.',
    tags: ['Verification API', 'PDF Automation', 'Access Control'],
  },
]

const nagarTags = ['Python', 'Flask', 'Hugging Face', 'gTTS', 'SpeechRecognition', 'RAG', 'RESTful API', 'Ngrok']

const academic = [
  {
    type: 'Social App',
    title: 'MithoMitho — Food Social Platform',
    desc: 'Food-focused social application built with Python Flask. Community engagement workflows, food discovery, and user-driven content sharing.',
    tags: ['Python Flask', 'Web Development', 'Social UI'],
  },
  {
    type: 'Full-Stack Platform',
    title: 'Structured Q&A Platform',
    desc: 'Community-based Q&A platform with voting systems, categories, and real-time updates.',
    tags: ['Full-Stack', 'Database Design', 'User Auth'],
  },
  {
    type: 'System Software',
    title: 'C-Based Account Management System',
    desc: 'Secure and efficient account management system focused on memory efficiency, file-based data persistence, and algorithmic problem-solving.',
    tags: ['C Programming', 'File I/O', 'Data Persistence'],
  },
]
</script>

<style scoped>
.section { padding: 2.5rem 0; }

.group-heading {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  font-family: var(--font-mono);
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--text-3);
  margin-bottom: 0.5rem;
}
.group-line {
  flex: 1;
  height: 1px;
  background: var(--border);
}

/* List container */
.projects-list {
  display: flex;
  flex-direction: column;
  width: 100%;
}

/* Each flat row */
.project-row,
.featured-row {
  display: grid;
  grid-template-columns: 220px 1fr;
  gap: 1.5rem;
  align-items: start;
  width: 100%;
  padding: 1.1rem 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.2s;
}
.project-row:first-child,
.featured-row { border-top: 1px solid var(--border); }

.project-row:hover,
.featured-row:hover {
  background: var(--teal-dim);
  border-radius: var(--radius);
  padding-left: 0.6rem;
  padding-right: 0.6rem;
}

.project-row:last-child { border-bottom: none; }

/* Featured styling */
.featured-row {
  border-top: 1px solid var(--teal-glow);
  border-bottom: 1px solid var(--teal-glow);
  margin-bottom: 0;
}

/* Left col */
.row-left {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  padding-top: 0.1rem;
}

/* Right col */
.row-right {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.project-type {
  font-family: var(--font-mono);
  font-size: 10px;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--teal);
}

.feat-label {
  font-family: var(--font-mono);
  font-size: 10px;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--amber);
}

.project-title {
  font-family: var(--font-head);
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--text-1);
  line-height: 1.3;
}
.project-title.large { font-size: 1rem; }

.project-desc {
  font-size: 13px;
  color: var(--text-2);
  line-height: 1.65;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
}

/* Collapse on small screens */
@media (max-width: 768px) {
  .project-row,
  .featured-row {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }
}
</style>