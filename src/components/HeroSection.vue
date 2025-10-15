<template>
  <section id="home" class="hero-section">
    <div class="hero-background">
      <div class="gradient-overlay"></div>
      <div class="particles" v-for="n in 50" :key="n" :style="particleStyle(n)"></div>
    </div>
    
    <div class="container hero-content">
      <div class="hero-text">
        <div class="greeting" data-aos="fade-up">
          <span class="wave">👋</span>
          <span>Hello, I'm</span>
        </div>
        
        <h1 class="hero-title" data-aos="fade-up" data-aos-delay="100">
          Kim Rynel <span class="highlight">Ellorico</span>
        </h1>
        
        <div class="typing-wrapper" data-aos="fade-up" data-aos-delay="200">
          <h2 class="hero-subtitle">
            <span class="typing-text">{{ currentText }}</span>
            <span class="cursor">|</span>
          </h2>
        </div>
        
        <p class="hero-description" data-aos="fade-up" data-aos-delay="300">
          Crafting scalable web applications with <strong>Laravel</strong>, <strong>Vue.js</strong>, 
          and <strong>REST APIs</strong>. Passionate about building solutions that make a difference.
        </p>
        
        <div class="hero-buttons" data-aos="fade-up" data-aos-delay="400">
          <a href="#projects" class="btn btn-hero btn-primary">
            <i class="bi bi-eye me-2"></i>
            View My Work
          </a>
          <a href="#contact" class="btn btn-hero btn-outline">
            <i class="bi bi-send me-2"></i>
            Get In Touch
          </a>
        </div>
        
        <div class="scroll-indicator" data-aos="fade-up" data-aos-delay="600">
          <a href="#about">
            <div class="mouse">
              <div class="wheel"></div>
            </div>
            <span>Scroll Down</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const texts = [
  'Full-Stack Developer',
  'Laravel Expert',
  'Vue.js Enthusiast',
  'API Architect',
  'Problem Solver'
]

const currentText = ref('')
let textIndex = 0
let charIndex = 0
let isDeleting = false
let typingTimer

const typeText = () => {
  const fullText = texts[textIndex]
  
  if (isDeleting) {
    currentText.value = fullText.substring(0, charIndex - 1)
    charIndex--
  } else {
    currentText.value = fullText.substring(0, charIndex + 1)
    charIndex++
  }
  
  let typingSpeed = isDeleting ? 50 : 100
  
  if (!isDeleting && charIndex === fullText.length) {
    typingSpeed = 2000
    isDeleting = true
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false
    textIndex = (textIndex + 1) % texts.length
    typingSpeed = 500
  }
  
  typingTimer = setTimeout(typeText, typingSpeed)
}

const particleStyle = (n) => {
  return {
    left: Math.random() * 100 + '%',
    top: Math.random() * 100 + '%',
    animationDelay: Math.random() * 5 + 's',
    animationDuration: (Math.random() * 10 + 10) + 's'
  }
}

onMounted(() => {
  typeText()
})

onUnmounted(() => {
  clearTimeout(typingTimer)
})
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: 120px 0 80px;
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #0d1b2a 0%, #1b263b 50%, #2d3250 100%);
  z-index: -1;
}

.gradient-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 20% 50%, rgba(102, 126, 234, 0.15) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(118, 75, 162, 0.15) 0%, transparent 50%);
}

.particles {
  position: absolute;
  width: 2px;
  height: 2px;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  animation: float linear infinite;
}

@keyframes float {
  0% {
    transform: translateY(0) translateX(0);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) translateX(100px);
    opacity: 0;
  }
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-text {
  text-align: center;
  color: white;
  max-width: 900px;
  margin: 0 auto;
}

.greeting {
  font-size: 1.5rem;
  font-weight: 500;
  margin-bottom: 1rem;
  opacity: 0.9;
}

.wave {
  display: inline-block;
  animation: wave 2s infinite;
  margin-right: 0.5rem;
}

@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(14deg); }
  20% { transform: rotate(-8deg); }
  40% { transform: rotate(-4deg); }
  50% { transform: rotate(10deg); }
}

.hero-title {
  font-size: clamp(2.5rem, 8vw, 4.5rem);
  font-weight: 800;
  margin-bottom: 1rem;
  line-height: 1.2;
}

.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.typing-wrapper {
  min-height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.hero-subtitle {
  font-size: clamp(1.5rem, 4vw, 2rem);
  font-weight: 600;
  color: rgba(255, 255, 255, 0.9);
  display: inline-block;
}

.typing-text {
  color: #667eea;
}

.cursor {
  color: #764ba2;
  animation: blink 0.7s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.hero-description {
  font-size: 1.15rem;
  color: rgba(255, 255, 255, 0.8);
  max-width: 700px;
  margin: 0 auto 2.5rem;
  line-height: 1.8;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn-hero {
  padding: 1rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  border-radius: 50px;
  transition: all 0.3s ease;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  border: 2px solid transparent;
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
  color: white;
}

.btn-outline {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
}

.btn-outline:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: white;
  transform: translateY(-3px);
  color: white;
}

.scroll-indicator {
  margin-top: 4rem;
  opacity: 0.7;
  transition: opacity 0.3s ease;
}

.scroll-indicator:hover {
  opacity: 1;
}

.scroll-indicator a {
  color: white;
  text-decoration: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
}

.mouse {
  width: 26px;
  height: 40px;
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 20px;
  position: relative;
  animation: bounce 2s infinite;
}

.wheel {
  width: 4px;
  height: 8px;
  background: white;
  border-radius: 2px;
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 2s infinite;
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(10px); }
}

@keyframes scroll {
  0% { opacity: 1; top: 8px; }
  100% { opacity: 0; top: 24px; }
}

@media (max-width: 768px) {
  .hero-section {
    padding: 100px 0 60px;
  }

  .greeting {
    font-size: 1.2rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .btn-hero {
    padding: 0.875rem 1.75rem;
    font-size: 1rem;
  }

  .hero-buttons {
    gap: 0.75rem;
  }
}
</style>