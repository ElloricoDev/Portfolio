<template>
  <section id="about" class="about-section">
    <div class="container">
      <div class="section-header text-center mb-5" data-aos="fade-up">
        <span class="section-label">Get To Know Me</span>
        <h2 class="section-title">About Me</h2>
        <div class="section-divider"></div>
      </div>

      <div class="row align-items-center g-5">
        <!-- Left Column: Image -->
        <div class="col-lg-5" data-aos="fade-right" data-aos-delay="100">
          <div class="profile-card">
            <div class="profile-image-wrapper">
              <div class="profile-ring"></div>
              <img 
                src="https://scontent.fmnl13-4.fna.fbcdn.net/v/t39.30808-6/558915513_122314245026223416_3369595040877646549_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=6ee11a&_nc_eui2=AeHfwKpLtb4viZ2i9iwYVHuztx3vTauZKPG3He9Nq5ko8c4QW4eFjG3vY9LGOzoi1R9SrCNwObypZKWOUtugm8Er&_nc_ohc=8jWrOpLqiXgQ7kNvwEejujQ&_nc_oc=Adl3e5jOaxFnx3kubefgP_VjD9CcxsaSBQbJdvCe3n3R5vyxG9L-JaAlLbEiqiX2T1SOK0WU6th8BohE23HSnvKF&_nc_zt=23&_nc_ht=scontent.fmnl13-4.fna&_nc_gid=2y3JdtuDOFN7ahyhfur0lw&oh=00_Afc0FLhJH7AFBjCIW_yrvWwagv72MvL4bhcUZvACgtd-Dg&oe=68F452DB" 
                alt="Kim Rynel Ellorico" 
                class="profile-image"
              />
              <div class="status-badge">
                <span class="status-dot"></span>
                Available for work
              </div>
            </div>
            
            <div class="profile-stats">
              <div class="stat-item" v-for="(stat, index) in stats" :key="index">
                <div class="stat-value">{{ stat.value }}</div>
                <div class="stat-label">{{ stat.label }}</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column: Description -->
        <div class="col-lg-7" data-aos="fade-left" data-aos-delay="200">
          <div class="about-content">
            <h3 class="about-greeting">
              Hi there! I'm <span class="text-gradient">Kim Rynel Ellorico</span> 
              <span class="wave-hand">👋</span>
            </h3>
            
            <p class="about-lead">
              I'm a passionate <strong>Full-Stack Developer</strong> with a focus on creating 
              innovative web solutions that make a real impact on communities.
            </p>
            
            <p class="about-text">
              Specializing in building scalable <strong>Laravel APIs</strong> and crafting 
              modern, responsive interfaces with <strong>Vue.js</strong> and <strong>React</strong>. 
              My journey in development is driven by the desire to solve real-world problems through 
              elegant code and thoughtful design.
            </p>
            
            <div class="highlight-box">
              <i class="bi bi-star-fill highlight-icon"></i>
              <div>
                <h5 class="mb-2">Featured Project: eBaryoLibrary</h5>
                <p class="mb-0">
                  A comprehensive web-based eBook library system designed to empower schools 
                  and barangays with accessible digital resources.
                </p>
              </div>
            </div>

            <div class="info-grid">
              <div class="info-item" v-for="(info, index) in contactInfo" :key="index">
                <i :class="`bi ${info.icon} info-icon`"></i>
                <div class="info-content">
                  <div class="info-label">{{ info.label }}</div>
                  <div class="info-value">{{ info.value }}</div>
                </div>
              </div>
            </div>

            <div class="tech-stack">
              <h6 class="tech-stack-title">Tech Stack</h6>
              <div class="tech-badges">
                <span class="tech-badge" v-for="(tech, index) in techStack" :key="index">
                  {{ tech }}
                </span>
              </div>
            </div>

            <a href="#projects" class="btn btn-about">
              <i class="bi bi-kanban me-2"></i>
              Explore My Projects
              <i class="bi bi-arrow-right ms-2"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { value: '3+', label: 'Years Experience' },
  { value: '15+', label: 'Projects Built' },
  { value: '100%', label: 'Client Satisfaction' }
]

const contactInfo = [
  { icon: 'bi-geo-alt-fill', label: 'Location', value: 'Philippines' },
  { icon: 'bi-envelope-fill', label: 'Email', value: 'kimrynelellorico05@gmail.com' },
  { icon: 'bi-code-slash', label: 'Expertise', value: 'Full-Stack Development' }
]

const techStack = ['Laravel', 'Vue.js', 'React', 'MySQL', 'REST API', 'Git', 'JavaScript', 'Bootstrap']
</script>

<style scoped>
.about-section {
  padding: 100px 0;
  background: linear-gradient(180deg, #f8f9fa 0%, #ffffff 100%);
  position: relative;
}

.section-header {
  margin-bottom: 4rem;
}

.section-label {
  display: inline-block;
  padding: 0.5rem 1.5rem;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 50px;
  color: #667eea;
  font-weight: 600;
  font-size: 0.9rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.section-title {
  font-size: clamp(2rem, 5vw, 3rem);
  font-weight: 800;
  color: #1b263b;
  margin-bottom: 1rem;
}

.section-divider {
  width: 80px;
  height: 4px;
  background: linear-gradient(90deg, #667eea, #764ba2);
  margin: 0 auto;
  border-radius: 2px;
}

.profile-card {
  position: relative;
}

.profile-image-wrapper {
  position: relative;
  width: 100%;
  max-width: 400px;
  margin: 0 auto 2rem;
}

.profile-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 50%;
  animation: rotate 10s linear infinite;
  z-index: -1;
}

@keyframes rotate {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.profile-image {
  width: 100%;
  aspect-ratio: 1;
  object-fit: cover;
  border-radius: 50%;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
  border: 8px solid white;
}

.status-badge {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  background: white;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 600;
  font-size: 0.9rem;
  color: #1b263b;
}

.status-dot {
  width: 10px;
  height: 10px;
  background: #10b981;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

.profile-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  background: white;
  padding: 2rem 1rem;
  border-radius: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.stat-item {
  text-align: center;
}

.stat-value {
  font-size: 2rem;
  font-weight: 800;
  background: linear-gradient(135deg, #667eea, #764ba2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.25rem;
}

.stat-label {
  font-size: 0.85rem;
  color: #6c757d;
  font-weight: 500;
}

.about-content {
  padding-left: 2rem;
}

.about-greeting {
  font-size: 1.75rem;
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1.5rem;
}

.text-gradient {
  background: linear-gradient(135deg, #667eea, #764ba2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.wave-hand {
  display: inline-block;
  animation: wave 2s ease-in-out infinite;
}

.about-lead {
  font-size: 1.25rem;
  font-weight: 600;
  color: #1b263b;
  line-height: 1.8;
  margin-bottom: 1rem;
}

.about-text {
  font-size: 1.05rem;
  color: #6c757d;
  line-height: 1.8;
  margin-bottom: 2rem;
}

.highlight-box {
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  padding: 1.5rem;
  border-radius: 15px;
  border-left: 4px solid #667eea;
  margin-bottom: 2rem;
  display: flex;
  gap: 1rem;
}

.highlight-icon {
  color: #667eea;
  font-size: 1.5rem;
  flex-shrink: 0;
}

.highlight-box h5 {
  color: #1b263b;
  font-weight: 700;
}

.highlight-box p {
  color: #6c757d;
  font-size: 0.95rem;
  line-height: 1.6;
}

.info-grid {
  display: grid;
  gap: 1rem;
  margin-bottom: 2rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: white;
  border-radius: 12px;
  transition: all 0.3s ease;
}

.info-item:hover {
  transform: translateX(5px);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.info-icon {
  font-size: 1.5rem;
  color: #667eea;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 10px;
  flex-shrink: 0;
}

.info-content {
  flex: 1;
}

.info-label {
  font-size: 0.85rem;
  color: #6c757d;
  font-weight: 500;
  margin-bottom: 0.25rem;
}

.info-value {
  font-size: 1rem;
  color: #1b263b;
  font-weight: 600;
}

.tech-stack {
  margin-bottom: 2rem;
}

.tech-stack-title {
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1rem;
}

.tech-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.tech-badge {
  padding: 0.5rem 1rem;
  background: white;
  border: 2px solid #e9ecef;
  border-radius: 50px;
  font-size: 0.9rem;
  font-weight: 600;
  color: #1b263b;
  transition: all 0.3s ease;
}

.tech-badge:hover {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-color: transparent;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
}

.btn-about {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 1rem 2rem;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  transition: all 0.3s ease;
  border: none;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
}

.btn-about:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
  color: white;
}

@media (max-width: 991px) {
  .about-content {
    padding-left: 0;
    margin-top: 2rem;
  }

  .profile-stats {
    margin-bottom: 2rem;
  }
}

@media (max-width: 576px) {
  .profile-stats {
    grid-template-columns: 1fr;
  }

  .stat-value {
    font-size: 1.75rem;
  }
}

/* Additional responsive adjustments */
@media (max-width: 768px) {
  .about-section {
    padding: 60px 0;
  }

  .section-header {
    margin-bottom: 3rem;
  }

  .profile-image-wrapper {
    max-width: 280px;
  }

  .status-badge {
    bottom: 20px;
    padding: 0.6rem 1.2rem;
    font-size: 0.8rem;
  }

  .about-greeting {
    font-size: 1.5rem;
  }

  .about-lead {
    font-size: 1.1rem;
  }

  .about-text {
    font-size: 1rem;
  }

  .highlight-box {
    flex-direction: column;
    padding: 1.25rem;
  }

  .info-item {
    padding: 0.875rem;
  }

  .tech-badges {
    gap: 0.5rem;
  }

  .tech-badge {
    padding: 0.4rem 0.875rem;
    font-size: 0.85rem;
  }

  .btn-about {
    width: 100%;
    justify-content: center;
    padding: 0.875rem 1.5rem;
  }
}

/* Extra animations for enhanced UX */
@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(14deg); }
  20% { transform: rotate(-8deg); }
  40% { transform: rotate(-4deg); }
  50% { transform: rotate(10deg); }
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.profile-image-wrapper {
  animation: float 6s ease-in-out infinite;
}

/* Accessibility improvements */
.info-item:focus-within {
  outline: 2px solid #667eea;
  outline-offset: 2px;
}

.tech-badge:focus {
  outline: 2px solid #667eea;
  outline-offset: 2px;
}

/* Print styles */
@media print {
  .profile-ring {
    display: none;
  }

  .status-badge {
    position: static;
    transform: none;
    margin-top: 1rem;
  }

  .btn-about {
    display: none;
  }

  * {
    animation: none !important;
    transition: none !important;
  }
}

/* Loading state for image */
.profile-image {
  opacity: 1;
  transition: opacity 0.5s ease-in;
}

.profile-image:not([src]),
.profile-image[src=""] {
  opacity: 0;
}

/* Smooth entrance animation */
@keyframes slideInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.about-content > * {
  animation: slideInUp 0.6s ease-out backwards;
}

.about-content > *:nth-child(1) { animation-delay: 0.1s; }
.about-content > *:nth-child(2) { animation-delay: 0.2s; }
.about-content > *:nth-child(3) { animation-delay: 0.3s; }
.about-content > *:nth-child(4) { animation-delay: 0.4s; }
.about-content > *:nth-child(5) { animation-delay: 0.5s; }
.about-content > *:nth-child(6) { animation-delay: 0.6s; }
.about-content > *:nth-child(7) { animation-delay: 0.7s; }

/* High contrast mode support */
@media (prefers-contrast: high) {
  .section-label,
  .text-gradient,
  .stat-value {
    -webkit-text-fill-color: initial;
    background: none;
    color: #667eea;
  }

  .info-item,
  .tech-badge {
    border: 2px solid currentColor;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }

  .profile-ring {
    animation: none;
  }

  .wave-hand {
    animation: none;
  }

  .status-dot {
    animation: none;
  }

  .profile-image-wrapper {
    animation: none;
  }
}

/* Dark mode support (if implemented) */
@media (prefers-color-scheme: dark) {
  .about-section {
    background: linear-gradient(180deg, #1a1a2e 0%, #16213e 100%);
  }

  .section-title,
  .about-greeting,
  .info-value {
    color: #ffffff;
  }

  .about-lead,
  .about-text,
  .highlight-box p,
  .info-label,
  .stat-label {
    color: #b8b8b8;
  }

  .profile-stats,
  .info-item {
    background: #1e2a3a;
  }

  .tech-badge {
    background: #1e2a3a;
    border-color: #2c3e50;
    color: #ffffff;
  }

  .highlight-box {
    background: rgba(102, 126, 234, 0.15);
  }

  .highlight-box h5 {
    color: #ffffff;
  }

  .status-badge {
    background: #1e2a3a;
    color: #ffffff;
  }
}
</style>