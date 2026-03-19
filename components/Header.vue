<template>
  <aside class="sidebar">
    <!-- Profile Block -->
    <div class="profile fade-up">
      <div class="avatar-wrap">
        <img src="https://www.shutterstock.com/image-photo/head-shot-beautiful-young-indian-260nw-2592061439.jpg" alt="Aastha Paudel" class="avatar" />
        <div class="avatar-ring" />
      </div>
      <h1 class="name">Aastha Paudel</h1>
      <p class="role">AI &amp; ML Researcher</p>

      <div class="contact-links">

        <!-- Email -->
        <a
            :href="emailRevealed ? 'mailto:aasthapdl121@gmail.com' : '#'"
            class="contact-item"
            :title="emailRevealed ? 'aasthapdl121@gmail.com' : 'Click to reveal email'"
            @click.prevent="revealEmail"
        >
          <span class="icon">✉</span>
          <span class="contact-text" :class="{ animating: emailAnimating }">{{ displayEmail }}</span>
        </a>

        <!-- GitHub -->
        <a href="https://github.com/Aasthapaudel" target="_blank" class="contact-item">
          <span class="icon">⌥</span>
          <span>github.com/Aasthapaudel</span>
        </a>

        <!-- LinkedIn -->
        <a href="https://www.linkedin.com/in/aastha-paudel-1b3b001b9/" target="_blank" class="contact-item">
          <span class="icon">↗</span>
          <span>LinkedIn</span>
        </a>

        <!-- Google Scholar -->
        <a href="https://scholar.google.com" target="_blank" class="contact-item">
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
  </aside>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// ── Nav ────────────────────────────────────────────────
const navItems = [
  { id: 'about',      label: 'About' },
  { id: 'research',   label: 'Research' },
  { id: 'projects',   label: 'Projects' },
  { id: 'skills',     label: 'Skills' },
  { id: 'education',  label: 'Education' },
  { id: 'experience', label: 'Experience' },
  { id: 'awards',     label: 'Awards' },
  // { id: 'blog',       label: 'Blog' },
]

const active = ref('about')
function setActive(id) { active.value = id }

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

// ── Scramble / Reveal ──────────────────────────────────
const REAL_EMAIL = 'aasthapdl121@gmail.com'
const CHARS      = 'abcdefghijklmnopqrstuvwxyz0123456789!#$%&*?'

const emailRevealed  = ref(false)
const emailAnimating = ref(false)
const displayEmail   = ref('')

function randomChar(original) {
  if (['@', '.', '+', ' ', '-', '_'].includes(original)) return original
  return CHARS[Math.floor(Math.random() * CHARS.length)]
}

function makeRandom(template) {
  return template.split('').map(randomChar).join('')
}

let shuffleInterval = null
let shuffleTimeout  = null
let frozenEmail     = ''

function startShuffle() {
  displayEmail.value   = makeRandom(REAL_EMAIL)
  emailAnimating.value = true

  shuffleInterval = setInterval(() => {
    displayEmail.value = makeRandom(REAL_EMAIL)
  }, 80)

  // After 2s — stop and freeze on whatever random string it landed on
  shuffleTimeout = setTimeout(() => {
    clearInterval(shuffleInterval)
    shuffleInterval      = null
    frozenEmail          = displayEmail.value   // save the frozen hash
    emailAnimating.value = false
  }, 2000)
}

function stopShuffle() {
  clearInterval(shuffleInterval)
  clearTimeout(shuffleTimeout)
  shuffleInterval = null
  shuffleTimeout  = null
}

// Click → animate char-by-char from frozen hash → real email
function revealEmail() {
  if (emailRevealed.value) {
    window.location.href = 'mailto:aasthapdl121@gmail.com'
    return
  }

  // If still shuffling, stop it first
  stopShuffle()
  emailAnimating.value = true

  const target  = REAL_EMAIL.split('')
  // Start from whatever is currently displayed (frozen or mid-shuffle)
  const current = displayEmail.value.padEnd(REAL_EMAIL.length, randomChar('x')).split('')
  let   step    = 0

  const interval = setInterval(() => {
    // Lock characters one by one left-to-right
    // Meanwhile keep randomising the unlocked ones for ~3 passes each
    for (let i = 0; i < target.length; i++) {
      if (i < step) {
        current[i] = target[i]           // locked ✓
      } else {
        current[i] = randomChar(target[i]) // still dancing
      }
    }
    displayEmail.value = current.join('')
    step++

    if (step > target.length) {
      clearInterval(interval)
      displayEmail.value   = REAL_EMAIL
      emailRevealed.value  = true
      emailAnimating.value = false
    }
  }, 45)
}

onMounted(() => startShuffle())
onUnmounted(() => stopShuffle())
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
  width: 160px;
  height: 160px;
  margin-bottom: 1rem;
}
.avatar {
  width: 160px;
  height: 160px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid var(--teal-glow);
  display: block;
}
.avatar-ring {
  position: absolute;
  inset: -6px;
  border-radius: 50%;
  border: 1.5px dashed var(--teal-glow);
  animation: spin 20s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }

.name {
  font-family: var(--font-head);
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-1);
  line-height: 1.2;
  margin-top: 0.2rem;
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
  cursor: pointer;
}
.contact-item:hover { color: var(--teal); }

.contact-text {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: 0.02em;
  transition: color 0.3s;
}
.contact-text.animating {
  color: var(--teal);
}

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
  .avatar-wrap { width: 80px; height: 80px; margin-bottom: 0; }
  .avatar { width: 80px; height: 80px; }
  .contact-links { display: none; }
  .nav { flex-direction: row; flex-wrap: wrap; }
}
</style>