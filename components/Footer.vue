<template>
  <footer class="footer">
    <div class="footer-inner">
      <span class="footer-name">Aastha Paudel</span>
      <span class="footer-copy">© {{ year }} · All Rights Reserved</span>
      <div class="footer-links">
        <a href="https://github.com/Aasthapaudel" target="_blank">GitHub</a>
        <a href="https://www.linkedin.com/in/aastha-paudel-1b3b001b9/" target="_blank">LinkedIn</a>
        <a href="mailto:aasthapdl121@gmail.com">Email</a>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  padding: 1.4rem 2rem;
  background: var(--bg2);
}
.footer-inner {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}
.footer-name {
  font-family: var(--font-head);
  font-size: 13px;
  font-weight: 600;
  color: var(--text-1);
}
.footer-copy {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-3);
}
.footer-links {
  display: flex;
  gap: 1rem;
  margin-left: auto;
}
.footer-links a {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-3);
  transition: color 0.2s;
}
.footer-links a:hover { color: var(--teal); }
</style>