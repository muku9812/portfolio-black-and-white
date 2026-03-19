<template>
  <div class="layout">
    <Header />
    <main class="main-content">
      <div class="content-inner">
        <Hero />
        <About />
        <Projects />
        <Skills />
        <Education />
<!--        <Blog />-->
<!--        <Contact />-->
      </div>
      <Footer />
    </main>
  </div>
</template>

<script setup>
useHead({
  title: 'Aastha Paudel — AI & ML Researcher',
})
</script>

<style scoped>
.main-content {
  flex: 1;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.content-inner {
  flex: 1;
  width: 100%;
  max-width: 100%;        /* ← was 820px, this was the culprit */
  padding: 0 3rem 2rem;
}
@media (max-width: 1024px) {
  .content-inner { padding: 0 2rem 2rem; }
}
@media (max-width: 768px) {
  .content-inner { padding: 0 1.2rem 2rem; }
}
</style>