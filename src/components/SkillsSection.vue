<template>
  <section id="skills" class="skills-section">
    <div class="container">
      <div class="section-header text-center mb-5" data-aos="fade-up">
        <span class="section-label">What I Do Best</span>
        <h2 class="section-title">Skills & Expertise</h2>
        <div class="section-divider"></div>
        <p class="section-description">
          A diverse skill set combining modern technologies to build powerful web applications.
        </p>
      </div>

      <div class="row g-4 mb-5">
        <div 
          class="col-lg-3 col-md-4 col-sm-6" 
          v-for="(skill, i) in skills" 
          :key="i"
          data-aos="zoom-in"
          :data-aos-delay="i * 50"
        >
          <div class="skill-card">
            <div class="skill-icon-wrapper">
              <i :class="skill.icon + ' skill-icon'"></i>
              <div class="icon-bg"></div>
            </div>
            <h6 class="skill-name">{{ skill.name }}</h6>
            <div class="skill-level">
              <div class="skill-bar">
                <div 
                  class="skill-progress" 
                  :style="{ width: skill.level + '%' }"
                ></div>
              </div>
              <span class="skill-percentage">{{ skill.level }}%</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Skill Categories -->
      <div class="skill-categories" data-aos="fade-up" data-aos-delay="400">
        <h3 class="categories-title text-center mb-4">Skill Categories</h3>
        <div class="row g-4">
          <div 
            class="col-lg-4 col-md-6" 
            v-for="(category, idx) in categories" 
            :key="idx"
            data-aos="fade-up"
            :data-aos-delay="idx * 100"
          >
            <div class="category-card">
              <div class="category-icon">
                <i :class="category.icon"></i>
              </div>
              <h5 class="category-title">{{ category.title }}</h5>
              <p class="category-description">{{ category.description }}</p>
              <ul class="category-list">
                <li v-for="(item, i) in category.items" :key="i">
                  <i class="bi bi-check-circle-fill"></i>
                  {{ item }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  { name: 'Laravel', icon: 'bi bi-code-slash', level: 95 },
  { name: 'Vue.js', icon: 'bi bi-lightning-charge-fill', level: 90 },
  { name: 'REST API', icon: 'bi bi-diagram-3-fill', level: 92 },
  { name: 'MySQL', icon: 'bi bi-database-fill', level: 88 },
  { name: 'React', icon: 'bi bi-bootstrap-reboot', level: 85 },
  { name: 'Git', icon: 'bi bi-git', level: 90 },
  { name: 'JavaScript', icon: 'bi bi-braces-asterisk', level: 93 },
  { name: 'HTML & CSS', icon: 'bi bi-file-code-fill', level: 95 },
]

const categories = [
  {
    title: 'Backend Development',
    icon: 'bi bi-server',
    description: 'Building robust server-side applications and APIs',
    items: ['Laravel Framework', 'RESTful APIs', 'Database Design', 'Authentication & Security']
  },
  {
    title: 'Frontend Development',
    icon: 'bi bi-palette',
    description: 'Creating beautiful and responsive user interfaces',
    items: ['Vue.js & React', 'Responsive Design', 'Modern CSS', 'Component Architecture']
  },
  {
    title: 'Full-Stack Integration',
    icon: 'bi bi-layers',
    description: 'Seamlessly connecting frontend and backend',
    items: ['API Integration', 'State Management', 'Real-time Features', 'Performance Optimization']
  }
]
</script>

<style scoped>
.skills-section {
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
  margin: 0 auto 1.5rem;
  border-radius: 2px;
}

.section-description {
  font-size: 1.1rem;
  color: #6c757d;
  max-width: 600px;
  margin: 0 auto;
}

.skill-card {
  background: white;
  padding: 2rem 1.5rem;
  border-radius: 20px;
  text-align: center;
  border: 2px solid #f1f3f5;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  height: 100%;
  position: relative;
  overflow: hidden;
}

.skill-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.05), rgba(118, 75, 162, 0.05));
  opacity: 0;
  transition: opacity 0.4s ease;
}

.skill-card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 15px 40px rgba(102, 126, 234, 0.2);
  border-color: transparent;
}

.skill-card:hover::before {
  opacity: 1;
}

.skill-icon-wrapper {
  position: relative;
  width: 80px;
  height: 80px;
  margin: 0 auto 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon-bg {
  position: absolute;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 20px;
  transition: all 0.4s ease;
}

.skill-card:hover .icon-bg {
  background: linear-gradient(135deg, #667eea, #764ba2);
  transform: rotate(10deg) scale(1.1);
}

.skill-icon {
  font-size: 2.5rem;
  color: #667eea;
  position: relative;
  z-index: 1;
  transition: all 0.4s ease;
}

.skill-card:hover .skill-icon {
  color: white;
  transform: scale(1.1);
}

.skill-name {
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1rem;
  font-size: 1.1rem;
  position: relative;
  z-index: 1;
}

.skill-level {
  position: relative;
  z-index: 1;
}

.skill-bar {
  height: 8px;
  background: #f1f3f5;
  border-radius: 50px;
  overflow: hidden;
  margin-bottom: 0.5rem;
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, #667eea, #764ba2);
  border-radius: 50px;
  transition: width 1s ease-in-out;
  animation: fillBar 1.5s ease-in-out;
}

@keyframes fillBar {
  0% { width: 0; }
}

.skill-percentage {
  font-size: 0.85rem;
  font-weight: 600;
  color: #667eea;
}

.skill-categories {
  margin-top: 5rem;
}

.categories-title {
  font-size: 2rem;
  font-weight: 800;
  color: #1b263b;
  margin-bottom: 3rem;
}

.category-card {
  background: white;
  padding: 2.5rem;
  border-radius: 20px;
  height: 100%;
  border: 2px solid #f1f3f5;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.category-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, #667eea, #764ba2);
  transform: scaleY(0);
  transform-origin: top;
  transition: transform 0.4s ease;
}

.category-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 40px rgba(102, 126, 234, 0.15);
  border-color: transparent;
}

.category-card:hover::before {
  transform: scaleY(1);
}

.category-icon {
  width: 70px;
  height: 70px;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
  transition: all 0.3s ease;
}

.category-card:hover .category-icon {
  background: linear-gradient(135deg, #667eea, #764ba2);
  transform: rotate(5deg) scale(1.05);
}

.category-icon i {
  font-size: 2rem;
  color: #667eea;
  transition: color 0.3s ease;
}

.category-card:hover .category-icon i {
  color: white;
}

.category-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1rem;
}

.category-description {
  color: #6c757d;
  margin-bottom: 1.5rem;
  line-height: 1.7;
}

.category-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.category-list li {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 0;
  color: #1b263b;
  font-weight: 500;
  border-bottom: 1px solid #f1f3f5;
}

.category-list li:last-child {
  border-bottom: none;
}

.category-list i {
  color: #10b981;
  font-size: 1.1rem;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .skill-card {
    padding: 1.5rem 1rem;
  }

  .skill-icon-wrapper {
    width: 60px;
    height: 60px;
  }

  .skill-icon {
    font-size: 2rem;
  }

  .category-card {
    padding: 2rem 1.5rem;
  }
}
</style>