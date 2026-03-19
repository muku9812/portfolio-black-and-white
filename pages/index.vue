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
        <Blog />
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
}
.content-inner {
  flex: 1;
  padding: 0 3rem 2rem;
  max-width: 820px;
}
@media (max-width: 1024px) {
  .content-inner { padding: 0 2rem 2rem; }
}
@media (max-width: 768px) {
  .content-inner { padding: 0 1.2rem 2rem; }
}
</style>