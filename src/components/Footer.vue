<template>
  <footer class="footer-section">
    <div class="footer-content">
      <div class="container">
        <div class="row g-5">
          <!-- Brand Column -->
          <div class="col-lg-4 col-md-6">
            <div class="footer-brand">
              <div class="brand-wrapper">
                <div class="brand-icon">
                  <i class="bi bi-code-slash"></i>
                </div>
                <h4 class="brand-name">Kim Rynel Ellorico</h4>
              </div>
              <p class="brand-tagline">
                Full-Stack Developer crafting elegant solutions with modern technologies.
              </p>
              <div class="brand-status">
                <span class="status-indicator"></span>
                <span class="status-text">Available for freelance work</span>
              </div>
            </div>
          </div>

          <!-- Quick Links Column -->
          <div class="col-lg-2 col-md-6 col-6">
            <div class="footer-links">
              <h5 class="footer-title">Quick Links</h5>
              <ul class="links-list">
                <li v-for="(link, idx) in quickLinks" :key="idx">
                  <a :href="link.href">
                    <i class="bi bi-chevron-right"></i>
                    {{ link.text }}
                  </a>
                </li>
              </ul>
            </div>
          </div>

          <!-- Services Column -->
          <div class="col-lg-3 col-md-6 col-6">
            <div class="footer-links">
              <h5 class="footer-title">Services</h5>
              <ul class="links-list">
                <li v-for="(service, idx) in services" :key="idx">
                  <a href="#contact">
                    <i class="bi bi-chevron-right"></i>
                    {{ service }}
                  </a>
                </li>
              </ul>
            </div>
          </div>

          <!-- Connect Column -->
          <div class="col-lg-3 col-md-6">
            <div class="footer-connect">
              <h5 class="footer-title">Let's Connect</h5>
              <p class="connect-text">
                Follow me on social media and let's build something amazing together!
              </p>
              <div class="social-links">
                <a 
                  v-for="(social, idx) in socialLinks" 
                  :key="idx"
                  :href="social.url" 
                  target="_blank"
                  class="social-link"
                  :title="social.name"
                >
                  <i :class="social.icon"></i>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer Bottom -->
    <div class="footer-bottom">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-6 text-center text-md-start mb-3 mb-md-0">
            <p class="copyright-text mb-0">
              &copy; {{ new Date().getFullYear() }} 
              <strong class="gradient-text">Kim Rynel Ellorico</strong>. 
              All rights reserved.
            </p>
          </div>
          <div class="col-md-6 text-center text-md-end">
            <p class="built-with mb-0">
              Built with <i class="bi bi-heart-fill text-danger"></i> using 
              <strong>Vue 3</strong> & <strong>Bootstrap 5</strong>
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Back to Top Button -->
    <a href="#home" class="back-to-top" v-show="showBackToTop" @click.prevent="scrollToTop">
      <i class="bi bi-arrow-up"></i>
    </a>
  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const showBackToTop = ref(false)

const quickLinks = [
  { text: 'Home', href: '#home' },
  { text: 'About', href: '#about' },
  { text: 'Projects', href: '#projects' },
  { text: 'Skills', href: '#skills' },
  { text: 'Contact', href: '#contact' }
]

const services = [
  'Web Development',
  'API Development',
  'UI/UX Design',
  'Database Design'
]

const socialLinks = [
  { name: 'GitHub', icon: 'bi bi-github', url: 'https://github.com/ElloricoDev' },
  { name: 'LinkedIn', icon: 'bi bi-linkedin', url: 'https://linkedin.com/in/kimrynelellorico' },
  { name: 'Email', icon: 'bi bi-envelope-at-fill', url: 'mailto:kimrynelellorico05@gmail.com' },
  { name: 'Facebook', icon: 'bi bi-facebook', url: '#' }
]

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 300
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.footer-section {
  background: linear-gradient(135deg, #0d1b2a 0%, #1b263b 100%);
  color: rgba(255, 255, 255, 0.8);
  position: relative;
  overflow: hidden;
}

.footer-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 20% 50%, rgba(102, 126, 234, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(118, 75, 162, 0.1) 0%, transparent 50%);
  pointer-events: none;
}

.footer-content {
  padding: 80px 0 40px;
  position: relative;
  z-index: 1;
}

.footer-brand {
  padding-right: 2rem;
}

.brand-wrapper {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.brand-icon {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  color: white;
}

.brand-name {
  color: white;
  font-weight: 800;
  font-size: 1.5rem;
  margin: 0;
  background: linear-gradient(135deg, #ffffff, #e0e0e0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.brand-tagline {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
  margin-bottom: 1.5rem;
  font-size: 1rem;
}

.brand-status {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1.25rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 50px;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  width: fit-content;
}

.status-indicator {
  width: 10px;
  height: 10px;
  background: #10b981;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { 
    opacity: 1;
    transform: scale(1);
  }
  50% { 
    opacity: 0.5;
    transform: scale(1.1);
  }
}

.status-text {
  color: rgba(255, 255, 255, 0.9);
  font-weight: 500;
  font-size: 0.9rem;
}

.footer-title {
  color: white;
  font-weight: 700;
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 0.75rem;
}

.footer-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 40px;
  height: 3px;
  background: linear-gradient(90deg, #667eea, #764ba2);
  border-radius: 2px;
}

.links-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.links-list li {
  margin-bottom: 0.75rem;
}

.links-list a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
  font-weight: 500;
}

.links-list a:hover {
  color: white;
  padding-left: 0.5rem;
}

.links-list i {
  font-size: 0.8rem;
  transition: transform 0.3s ease;
}

.links-list a:hover i {
  transform: translateX(3px);
}

.connect-text {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
  margin-bottom: 1.5rem;
}

.social-links {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.social-link {
  width: 45px;
  height: 45px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.2rem;
  text-decoration: none;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-color: transparent;
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding: 2rem 0;
  position: relative;
  z-index: 1;
}

.copyright-text,
.built-with {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.95rem;
}

.gradient-text {
  background: linear-gradient(135deg, #667eea, #764ba2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 700;
}

.built-with strong {
  color: rgba(255, 255, 255, 0.9);
  font-weight: 600;
}

.back-to-top {
  position: fixed;
  bottom: 30px;
  right: 30px;
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  text-decoration: none;
  box-shadow: 0 4px 20px rgba(102, 126, 234, 0.4);
  transition: all 0.3s ease;
  z-index: 1000;
}

.back-to-top:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 30px rgba(102, 126, 234, 0.6);
  color: white;
}

@media (max-width: 991px) {
  .footer-content {
    padding: 60px 0 30px;
  }

  .footer-brand {
    padding-right: 0;
    margin-bottom: 2rem;
  }

  .footer-links,
  .footer-connect {
    margin-bottom: 2rem;
  }
}

@media (max-width: 576px) {
  .back-to-top {
    bottom: 20px;
    right: 20px;
    width: 45px;
    height: 45px;
  }

  .brand-wrapper {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>