<template>
  <div>
    <!-- ── Education ──────────────────────────────── -->
    <section id="education" class="section fade-up">
      <span class="section-label">// 05 — Education</span>
      <h2 class="section-title">Academic Journey</h2>

      <div class="timeline">
        <div v-for="(edu, i) in education" :key="i" class="timeline-item">
          <div class="tl-dot" />
          <div class="tl-body">
            <div class="tl-meta">
              <span class="tl-years">{{ edu.years }}</span>
              <span class="tl-badge" v-if="edu.badge">{{ edu.badge }}</span>
            </div>
            <h4 class="tl-title">{{ edu.degree }}</h4>
            <p class="tl-inst">{{ edu.institution }}</p>
            <ul class="tl-bullets">
              <li v-for="b in edu.bullets" :key="b">{{ b }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <div class="divider" />

    <!-- ── Experience ─────────────────────────────── -->
    <section id="experience" class="section fade-up">
      <span class="section-label">// 06 — Experience</span>
      <h2 class="section-title">Professional Experience</h2>

      <h3 class="sub-group">Professional Roles</h3>
      <div class="timeline">
        <div v-for="(exp, i) in experience" :key="i" class="timeline-item">
          <div class="tl-dot accent" />
          <div class="tl-body">
            <div class="tl-meta">
              <span class="tl-years">{{ exp.period }}</span>
              <span class="tl-badge amber" v-if="exp.current">● Current</span>
            </div>
            <h4 class="tl-title">{{ exp.role }}</h4>
            <p class="tl-inst">{{ exp.company }}</p>
            <ul class="tl-bullets">
              <li v-for="b in exp.bullets" :key="b">{{ b }}</li>
            </ul>
          </div>
        </div>
      </div>

      <h3 class="sub-group" style="margin-top:1.8rem">Leadership &amp; Volunteering</h3>
      <div class="timeline">
        <div v-for="(v, i) in volunteering" :key="i" class="timeline-item">
          <div class="tl-dot dim" />
          <div class="tl-body">
            <div class="tl-meta">
              <span class="tl-years">{{ v.period }}</span>
            </div>
            <h4 class="tl-title">{{ v.role }}</h4>
            <p class="tl-inst">{{ v.org }}</p>
            <ul class="tl-bullets">
              <li v-for="b in v.bullets" :key="b">{{ b }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <div class="divider" />

    <!-- ── Awards ─────────────────────────────────── -->
    <section id="awards" class="section fade-up">
      <span class="section-label">// 07 — Honors &amp; Awards</span>
      <h2 class="section-title">Recognition</h2>

      <div class="awards-list">
        <div v-for="a in awards" :key="a.title" class="award-row">
          <span class="award-icon">{{ a.icon }}</span>
          <div class="award-body">
            <h4 class="award-title">{{ a.title }}</h4>
            <p class="award-desc">{{ a.desc }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const education = [
  {
    years: '2020 — 2025',
    degree: 'Bachelor of Computer Engineering',
    institution: 'Institute of Engineering (IOE), Paschimanchal Campus, Tribhuvan University',
    badge: 'Graduated 2025',
    bullets: [
      'Focused on AI, Software Systems, and Distributed Computing.',
      'Practically engaged in Web Systems and Networking Research.',
      'Core concentration on Algorithms and Operating Systems.',
    ],
  },
  {
    years: '2018 — 2020',
    degree: 'Higher Secondary Education',
    institution: 'KIST College, Kathmandu',
    bullets: [
      'Specialised in Computer Science and Mathematics.',
      'Developed foundational analytical and problem-solving skills.',
    ],
  },
  {
    years: 'Graduated with Distinction',
    degree: 'Secondary Education (SEE)',
    institution: 'Amar Adarsha Boarding School, Baglung',
    bullets: [
      'Strong foundation in Mathematics and Science.',
      'Active participant in regional tech and science exhibitions.',
    ],
  },
]

const experience = [
  {
    period: 'May 2025 — Present',
    role: 'Laravel Developer',
    company: 'Trilokya Technology',
    current: true,
    bullets: [
      'Developed an Asset Management, Audit & Compliance System.',
      'Built reactive components using Laravel & Livewire with strong backend and database integration.',
      'Designed and optimised MySQL databases with complex joins, indexes, and raw SQL queries.',
      'Mentored juniors and interns; conducted code reviews and facilitated team collaboration.',
    ],
  },
  {
    period: 'Oct 2024 — May 2025',
    role: 'Laravel Developer',
    company: 'TukiSoft Pvt. Ltd',
    current: false,
    bullets: [
      'Contributed to a real-time Job Portal and LMS using Laravel and MySQL, focusing on scalable architecture.',
      'Developed dynamic, role-based dashboards and implemented secure authentication middleware and RBAC.',
    ],
  },
  {
    period: 'Jun 2024 — Nov 2024',
    role: 'Laravel Developer Intern',
    company: 'Xdezo Technology',
    current: false,
    bullets: [
      'Built a Certificate Management System using Laravel and MySQL — generation, validation, and admin control.',
      'Worked with MVC architecture and RESTful APIs to deliver robust software solutions.',
    ],
  },
]

const volunteering = [
  {
    period: 'Nov 2023 — Present',
    role: 'Microsoft Learn Student Ambassador',
    org: 'Microsoft',
    bullets: [
      'Organised workshops and demo projects on Azure, promoting cloud technologies.',
      'Demonstrated communication, teamwork, and mentorship through community engagement.',
    ],
  },
  {
    period: 'Jan 2023 — 2024',
    role: 'Vice Project Lead',
    org: 'Code For Change, Pokhara',
    bullets: [
      'Led tech initiatives and training programmes, collaborating with domain experts and student teams.',
      'Showcased leadership, coordination, and adaptability in managing community tech projects.',
    ],
  },
]

const awards = [
  {
    icon: '🏅',
    title: 'Mahatma Gandhi Scholar',
    desc: 'Awarded for Academic Excellence during undergraduate studies at IOE, Tribhuvan University.',
  },
  {
    icon: '📄',
    title: 'IEEE ICTP 2026 — Accepted Research',
    desc: 'Paper accepted at the IEEE International Conference on ICT and Photonics 2026 as Main Author & Presenter.',
  },
  {
    icon: '☁️',
    title: 'Microsoft Learn Student Ambassador',
    desc: 'Selected as MLSA — recognised for community contribution and technical leadership.',
  },
]
</script>

<style scoped>
.section { padding: 2.5rem 0; }

.sub-group {
  font-family: var(--font-mono);
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--text-3);
  margin-bottom: 0.5rem;
}

/* Timeline */
.timeline {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.timeline-item {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
  padding: 1.1rem 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.2s, padding 0.2s;
  width: 100%;
}
.timeline-item:first-child { border-top: 1px solid var(--border); }
.timeline-item:last-child  { border-bottom: none; }

.timeline-item:hover {
  background: var(--teal-dim);
  border-radius: var(--radius);
  padding-left: 0.6rem;
  padding-right: 0.6rem;
}

.tl-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--teal);
  margin-top: 0.45rem;
  flex-shrink: 0;
  box-shadow: 0 0 6px var(--teal-glow);
}
.tl-dot.accent { background: var(--amber); box-shadow: 0 0 6px rgba(217,119,6,0.3); }
.tl-dot.dim    { background: var(--text-3); box-shadow: none; }

.tl-body { flex: 1; width: 100%; }

.tl-meta {
  display: flex;
  align-items: center;
  gap: 0.7rem;
  margin-bottom: 0.3rem;
}
.tl-years {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-3);
}
.tl-badge {
  font-family: var(--font-mono);
  font-size: 10px;
  padding: 2px 8px;
  border-radius: 99px;
  background: var(--teal-dim);
  color: var(--teal);
  border: 1px solid var(--teal-glow);
}
.tl-badge.amber {
  background: rgba(217,119,6,0.08);
  color: var(--amber);
  border-color: rgba(217,119,6,0.25);
}

.tl-title {
  font-family: var(--font-head);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-1);
  margin-bottom: 0.1rem;
}
.tl-inst {
  font-size: 12.5px;
  color: var(--teal);
  margin-bottom: 0.4rem;
}
.tl-bullets { list-style: none; display: flex; flex-direction: column; gap: 0.2rem; }
.tl-bullets li {
  font-size: 13px;
  color: var(--text-2);
  padding-left: 1rem;
  position: relative;
}
.tl-bullets li::before {
  content: '—';
  position: absolute;
  left: 0;
  color: var(--text-3);
  font-size: 11px;
}

/* Awards flat rows */
.awards-list {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.award-row {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.1rem 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.2s, padding 0.2s;
}
.award-row:first-child { border-top: 1px solid var(--border); }
.award-row:last-child  { border-bottom: none; }

.award-row:hover {
  background: var(--teal-dim);
  border-radius: var(--radius);
  padding-left: 0.6rem;
  padding-right: 0.6rem;
}

.award-icon  { font-size: 1.4rem; flex-shrink: 0; }
.award-body  { flex: 1; }
.award-title {
  font-family: var(--font-head);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-1);
  margin-bottom: 0.2rem;
}
.award-desc { font-size: 13px; color: var(--text-2); }
</style>