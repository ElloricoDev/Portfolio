<template>
  <section id="projects" class="projects-section">
    <div class="container">
      <div class="section-header text-center mb-5" data-aos="fade-up">
        <span class="section-label">My Work</span>
        <h2 class="section-title">Featured Projects</h2>
        <div class="section-divider"></div>
        <p class="section-description">
          Explore some of my recent work showcasing full-stack development with Laravel, Vue.js, and more.
        </p>
      </div>

      <div class="row g-4">
        <div 
          class="col-lg-4 col-md-6" 
          v-for="(project, i) in projects" 
          :key="i"
          data-aos="fade-up"
          :data-aos-delay="i * 100"
        >
          <div class="project-card">
            <div class="project-header">
              <div class="project-icon">
                <i :class="project.icon"></i>
              </div>
              <div class="project-number">0{{ i + 1 }}</div>
            </div>

            <div class="project-content">
              <h5 class="project-title">{{ project.title }}</h5>
              <p class="project-description">{{ project.desc }}</p>

              <div class="project-tech">
                <span 
                  class="tech-tag" 
                  v-for="(tech, idx) in project.technologies" 
                  :key="idx"
                >
                  {{ tech }}
                </span>
              </div>
            </div>

            <div class="project-footer">
              <a
                :href="project.demo"
                target="_blank"
                class="project-link"
                :class="{ disabled: project.demo === '#' }"
              >
                <i class="bi bi-box-arrow-up-right"></i>
                <span>Live Demo</span>
              </a>
              <a
                :href="project.source"
                target="_blank"
                class="project-link"
                :class="{ disabled: project.source === '#' }"
              >
                <i class="bi bi-github"></i>
                <span>Source Code</span>
              </a>
            </div>

            <div class="project-overlay"></div>
          </div>
        </div>
      </div>

      <div class="text-center mt-5" data-aos="fade-up" data-aos-delay="400">
        <a href="https://github.com/ElloricoDev" target="_blank" class="btn btn-projects">
          <i class="bi bi-github me-2"></i>
          View All Projects on GitHub
          <i class="bi bi-arrow-right ms-2"></i>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    title: 'eBaryoLibrary',
    desc: 'A comprehensive web-based eBook library system designed to empower schools and barangays with accessible digital resources and efficient management.',
    demo: '#',
    source: 'https://github.com/kellorico/eBaryo-LibrarySystem',
    icon: 'bi bi-book',
    technologies: ['Laravel', 'MySQL', 'Bootstrap']
  },
  {
    title: 'TaskTrackr',
    desc: 'Modern task management application featuring a Laravel REST API backend and Vue.js frontend with real-time updates and collaboration tools.',
    demo: '#',
    source: '#',
    icon: 'bi bi-check2-square',
    technologies: ['Laravel', 'Vue.js', 'REST API']
  },
  {
    title: 'Portfolio Contact API',
    desc: 'Robust Laravel API for handling portfolio contact forms with validation, email notifications, and spam protection mechanisms.',
    demo: '#',
    source: '#',
    icon: 'bi bi-envelope-paper',
    technologies: ['Laravel', 'API', 'Mail']
  }
]
</script>

<style scoped>
.projects-section {
  padding: 100px 0;
  background: #ffffff;
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
  margin: 0 auto 1.5rem;
  border-radius: 2px;
}

.section-description {
  font-size: 1.1rem;
  color: #6c757d;
  max-width: 600px;
  margin: 0 auto;
}

.project-card {
  background: white;
  border-radius: 20px;
  padding: 2rem;
  height: 100%;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;
  border: 2px solid #f1f3f5;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, #667eea, #764ba2);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s ease;
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102, 126, 234, 0.2);
  border-color: transparent;
}

.project-card:hover::before {
  transform: scaleX(1);
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.05), rgba(118, 75, 162, 0.05));
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.project-icon {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.75rem;
  color: #667eea;
  transition: all 0.3s ease;
}

.project-card:hover .project-icon {
  transform: rotate(10deg) scale(1.1);
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
}

.project-number {
  font-size: 3rem;
  font-weight: 800;
  color: #f1f3f5;
  line-height: 1;
}

.project-content {
  flex: 1;
  margin-bottom: 1.5rem;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1rem;
  transition: color 0.3s ease;
}

.project-card:hover .project-title {
  color: #667eea;
}

.project-description {
  color: #6c757d;
  line-height: 1.7;
  margin-bottom: 1.5rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  padding: 0.4rem 0.9rem;
  background: #f8f9fa;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 600;
  color: #667eea;
  transition: all 0.3s ease;
}

.project-card:hover .tech-tag {
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.15), rgba(118, 75, 162, 0.15));
}

.project-footer {
  display: flex;
  gap: 1rem;
  padding-top: 1.5rem;
  border-top: 2px solid #f1f3f5;
}

.project-link {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  background: transparent;
  border: 2px solid #e9ecef;
  border-radius: 12px;
  color: #1b263b;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.project-link:hover:not(.disabled) {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border-color: transparent;
  transform: translateY(-2px);
}

.project-link.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

.btn-projects {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 1rem 2.5rem;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
  border: none;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
  font-size: 1.05rem;
}

.btn-projects:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
  color: white;
}

@media (max-width: 768px) {
  .project-card {
    padding: 1.5rem;
  }

  .project-number {
    font-size: 2rem;
  }

  .project-icon {
    width: 50px;
    height: 50px;
    font-size: 1.5rem;
  }
}
</style>