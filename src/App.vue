<template>
  <div class="app-wrapper" data-bs-spy="scroll" data-bs-target="#navbar" data-bs-offset="70" tabindex="0">
    <Navbar />
    <HeroSection />
    <AboutSection />
    <ProjectsSection />
    <SkillsSection />
    <ContactSection />
    <Footer />
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import Navbar from './components/NavbarSection.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'

onMounted(() => {
  // Initialize AOS (Animate On Scroll)
  if (typeof AOS !== 'undefined') {
    AOS.init({
      duration: 1000,
      easing: 'ease-out-cubic',
      once: true,
      offset: 100,
      delay: 50
    })
  }

  // Smooth scrolling for anchor links
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
      e.preventDefault()
      const target = document.querySelector(this.getAttribute('href'))
      if (target) {
        const offset = 80
        const targetPosition = target.offsetTop - offset
        window.scrollTo({
          top: targetPosition,
          behavior: 'smooth'
        })
      }
    })
  })

  // Add smooth reveal on page load
  document.body.style.opacity = '0'
  setTimeout(() => {
    document.body.style.transition = 'opacity 0.5s ease-in'
    document.body.style.opacity = '1'
  }, 100)
})
</script>

<style>
/* Global Styles */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --primary-color: #667eea;
  --secondary-color: #764ba2;
  --dark-color: #1b263b;
  --light-color: #f8f9fa;
  --text-color: #1b263b;
  --text-muted: #6c757d;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  color: var(--text-color);
  overflow-x: hidden;
  line-height: 1.6;
}

.app-wrapper {
  min-height: 100vh;
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, #667eea, #764ba2);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(180deg, #5568d3, #6a3f8f);
}

/* Selection */
::selection {
  background: rgba(102, 126, 234, 0.3);
  color: var(--dark-color);
}

::-moz-selection {
  background: rgba(102, 126, 234, 0.3);
  color: var(--dark-color);
}

/* Smooth transitions for all interactive elements */
a,
button,
input,
textarea,
select {
  transition: all 0.3s ease;
}

/* Focus styles */
a:focus,
button:focus,
input:focus,
textarea:focus,
select:focus {
  outline: 2px solid var(--primary-color);
  outline-offset: 2px;
}

/* Remove focus outline for mouse users */
a:focus:not(:focus-visible),
button:focus:not(:focus-visible),
input:focus:not(:focus-visible),
textarea:focus:not(:focus-visible),
select:focus:not(:focus-visible) {
  outline: none;
}

/* Smooth anchor scroll offset */
section {
  scroll-margin-top: 80px;
}

/* Loading animation for images */
img {
  transition: opacity 0.3s ease;
}

img:not([src]) {
  opacity: 0;
}

/* Utility classes */
.gradient-text {
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.text-shadow {
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.box-shadow {
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

/* Animation classes */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.fade-in {
  animation: fadeIn 0.6s ease-out;
}

.slide-in-left {
  animation: slideInLeft 0.6s ease-out;
}

.slide-in-right {
  animation: slideInRight 0.6s ease-out;
}

.scale-in {
  animation: scaleIn 0.6s ease-out;
}

/* Responsive typography */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
  
  h1 {
    font-size: 2rem;
  }
  
  h2 {
    font-size: 1.75rem;
  }
  
  h3 {
    font-size: 1.5rem;
  }
  
  h4 {
    font-size: 1.25rem;
  }
  
  h5 {
    font-size: 1.1rem;
  }
  
  h6 {
    font-size: 1rem;
  }
}

/* Print styles */
@media print {
  .navbar,
  .back-to-top,
  .contact-form {
    display: none;
  }
  
  * {
    color: black !important;
    background: white !important;
  }
}
</style>