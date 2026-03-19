<template>
  <section id="contact" class="section">
    <div class="container">
      <h2 class="section-title">Get in Touch</h2>
      <div class="contact-content">
        <p>I'm currently looking for new opportunities. Feel free to reach out via email or LinkedIn.</p>
        <div class="contact-links">
          <a href="mailto:aasthapaudel@example.com" class="contact-link">
            <span>Email Me</span>
          </a>
          <a href="https://linkedin.com/in/aasthapaudel" target="_blank" class="contact-link">
            <span>LinkedIn</span>
          </a>
          <a href="https://github.com/aasthapaudel" target="_blank" class="contact-link">
            <span>GitHub</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  padding: 80px 0;
  background-color: #f9f9f9;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}
.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 40px;
  color: #333;
}
.contact-content {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}
.contact-links {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 30px;
}
.contact-link {
  display: inline-block;
  padding: 12px 24px;
  background-color: #333;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}
.contact-link:hover {
  background-color: #555;
}
</style>
