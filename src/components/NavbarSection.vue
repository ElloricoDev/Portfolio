<template>
  <nav id="navbar" class="navbar navbar-expand-lg navbar-dark fixed-top" :class="{ 'scrolled': isScrolled }">
    <div class="container">
      <!-- Brand with Animation -->
      <a class="navbar-brand fw-bold d-flex align-items-center" href="#home">
        <div class="brand-icon-wrapper me-2">
          <i class="bi bi-code-slash brand-icon"></i>
        </div>
        <span class="brand-text">Kim Rynel Ellorico</span>
      </a>

      <!-- Toggle Button -->
      <button
        class="navbar-toggler border-0"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navmenu"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Navigation Links -->
      <div class="collapse navbar-collapse" id="navmenu">
        <ul class="navbar-nav ms-auto align-items-lg-center">
          <li class="nav-item" v-for="(link, index) in navLinks" :key="index">
            <a 
              :href="link.href" 
              class="nav-link d-flex align-items-center px-3 py-2"
              @click="setActive(link.href)"
            >
              <i :class="`bi ${link.icon} me-2`"></i>
              <span>{{ link.text }}</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)

const navLinks = [
  { href: '#home', icon: 'bi-house-door', text: 'Home' },
  { href: '#about', icon: 'bi-person', text: 'About' },
  { href: '#projects', icon: 'bi-kanban', text: 'Projects' },
  { href: '#skills', icon: 'bi-lightning-charge', text: 'Skills' },
  { href: '#contact', icon: 'bi-envelope', text: 'Contact' }
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const setActive = (href) => {
  // Close mobile menu on click
  const navMenu = document.getElementById('navmenu')
  if (navMenu.classList.contains('show')) {
    const toggler = document.querySelector('.navbar-toggler')
    toggler?.click()
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  background: rgba(13, 27, 42, 0.95);
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  padding: 1rem 0;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.navbar.scrolled {
  background: rgba(13, 27, 42, 0.98);
  padding: 0.5rem 0;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.brand-icon-wrapper {
  width: 35px;
  height: 35px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.navbar-brand:hover .brand-icon-wrapper {
  transform: rotate(360deg);
}

.brand-icon {
  color: white;
  font-size: 1.2rem;
}

.brand-text {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-size: 1.1rem;
  letter-spacing: 0.5px;
}

.nav-link {
  color: rgba(255, 255, 255, 0.85) !important;
  font-weight: 500;
  position: relative;
  transition: all 0.3s ease;
  border-radius: 8px;
  margin: 0 0.25rem;
}

.nav-link::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, #667eea, #764ba2);
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: white !important;
  background: rgba(255, 255, 255, 0.1);
}

.nav-link:hover::before {
  width: 70%;
}

.nav-link i {
  font-size: 1.1rem;
  transition: transform 0.3s ease;
}

.nav-link:hover i {
  transform: translateY(-2px);
}

.navbar-toggler {
  padding: 0.5rem;
  transition: all 0.3s ease;
}

.navbar-toggler:hover {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 8px;
}

.navbar-toggler:focus {
  box-shadow: 0 0 0 0.25rem rgba(102, 126, 234, 0.25);
}

@media (max-width: 991px) {
  .navbar-collapse {
    background: rgba(13, 27, 42, 0.98);
    padding: 1rem;
    border-radius: 12px;
    margin-top: 1rem;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  }

  .nav-link {
    margin: 0.25rem 0;
  }
}
</style>