<template>
  <aside class="sidebar">
    <!-- Profile Block -->
    <div class="profile fade-up">
      <div class="avatar-wrap">
        <img src="https://www.freepik.com/premium-vector/cute-woman-avatar-profile-vector-illustration_146713188.htm" alt="Aastha Paudel" class="avatar" />
        <div class="avatar-ring" />
      </div>
      <h1 class="name">Aastha Paudel</h1>
      <p class="role">AI &amp; ML Researcher</p>

      <div class="contact-links">
        <a href="mailto:aasthapdl121@gmail.com" class="contact-item" title="Email">
          <span class="icon">✉</span>
          <span>aasthapdl121@gmail.com</span>
        </a>
        <a href="https://github.com/Aasthapaudel" target="_blank" class="contact-item" title="GitHub">
          <span class="icon">⌥</span>
          <span>github.com/Aasthapaudel</span>
        </a>
        <a href="https://www.linkedin.com/in/aastha-paudel-1b3b001b9/" target="_blank" class="contact-item" title="LinkedIn">
          <span class="icon">↗</span>
          <span>LinkedIn</span>
        </a>
        <a href="https://scholar.google.com" target="_blank" class="contact-item" title="Google Scholar">
          <span class="icon">◈</span>
          <span>Google Scholar</span>
        </a>
      </div>
    </div>

    <!-- Navigation -->
    <nav class="nav fade-up" style="animation-delay:0.1s">
      <a
          v-for="item in navItems"
          :key="item.id"
          :href="`#${item.id}`"
          class="nav-item"
          :class="{ active: active === item.id }"
          @click="setActive(item.id)"
      >
        <span class="nav-dot" />
        {{ item.label }}
      </a>
    </nav>

    <!-- Footer credit -->
    <p class="sidebar-credit">
      Inspired by
      <a href="https://jonbarron.info/" target="_blank">Jon Barron</a>
    </p>
  </aside>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const navItems = [
  { id: 'about',        label: 'About' },
  { id: 'research',     label: 'Research' },
  { id: 'projects',     label: 'Projects' },
  { id: 'skills',       label: 'Skills' },
  { id: 'education',    label: 'Education' },
  { id: 'experience',   label: 'Experience' },
  { id: 'awards',       label: 'Awards' },
  { id: 'blog',         label: 'Blog' },
  { id: 'contact',      label: 'Contact' },
]

const active = ref('about')

function setActive(id) {
  active.value = id
}

function onScroll() {
  for (const item of [...navItems].reverse()) {
    const el = document.getElementById(item.id)
    if (el && el.getBoundingClientRect().top <= 120) {
      active.value = item.id
      break
    }
  }
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.sidebar {
  position: sticky;
  top: 0;
  height: 100vh;
  width: var(--sidebar-w);
  min-width: var(--sidebar-w);
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  padding: 2.5rem 1.6rem 2rem;
  border-right: 1px solid var(--border);
  background: var(--bg2);
  gap: 1.8rem;
}

/* Profile */
.profile { display: flex; flex-direction: column; gap: 0.5rem; }

.avatar-wrap {
  position: relative;
  width: 88px;
  height: 88px;
  margin-bottom: 0.6rem;
}
.avatar {
  width: 88px;
  height: 88px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid var(--teal-glow);
  display: block;
}
.avatar-ring {
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  border: 1px dashed var(--teal-glow);
  animation: spin 20s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }

.name {
  font-family: var(--font-head);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-1);
  line-height: 1.2;
}
.role {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--teal);
  letter-spacing: 0.08em;
}

/* Contact links */
.contact-links { display: flex; flex-direction: column; gap: 0.35rem; margin-top: 0.5rem; }
.contact-item {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 11.5px;
  color: var(--text-2);
  transition: color 0.2s;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.contact-item:hover { color: var(--teal); }
.icon {
  font-size: 12px;
  color: var(--teal);
  flex-shrink: 0;
  width: 14px;
  text-align: center;
}

/* Nav */
.nav { display: flex; flex-direction: column; gap: 0.1rem; }

.nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 12.5px;
  font-family: var(--font-mono);
  letter-spacing: 0.05em;
  color: var(--text-3);
  padding: 5px 8px;
  border-radius: var(--radius);
  transition: color 0.2s, background 0.2s;
  text-transform: uppercase;
}
.nav-item:hover { color: var(--text-1); background: var(--teal-dim); }
.nav-item.active { color: var(--teal); background: var(--teal-dim); }

.nav-dot {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: currentColor;
  flex-shrink: 0;
  transition: transform 0.2s;
}
.nav-item.active .nav-dot { transform: scale(1.6); }

/* Credit */
.sidebar-credit {
  margin-top: auto;
  font-size: 11px;
  color: var(--text-3);
}
.sidebar-credit a { color: var(--text-3); text-decoration: underline; }

/* Mobile */
@media (max-width: 768px) {
  .sidebar {
    position: static;
    width: 100%;
    height: auto;
    border-right: none;
    border-bottom: 1px solid var(--border);
    padding: 1.5rem;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: 1rem;
  }
  .profile { flex-direction: row; align-items: center; gap: 1rem; }
  .avatar-wrap { width: 56px; height: 56px; margin-bottom: 0; }
  .avatar { width: 56px; height: 56px; }
  .contact-links { display: none; }
  .nav { flex-direction: row; flex-wrap: wrap; }
  .sidebar-credit { display: none; }
}
</style>