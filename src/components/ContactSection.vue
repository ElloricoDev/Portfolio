<template>
  <section id="contact" class="contact-section">
    <div class="container">
      <div class="section-header text-center mb-5" data-aos="fade-up">
        <span class="section-label">Let's Connect</span>
        <h2 class="section-title">Get In Touch</h2>
        <div class="section-divider"></div>
        <p class="section-description">
          Have a project in mind or want to collaborate? I'd love to hear from you!
        </p>
      </div>

      <div class="row g-5 align-items-start">
        <!-- Contact Info -->
        <div class="col-lg-5" data-aos="fade-right">
          <div class="contact-info-wrapper">
            <h3 class="info-title">Let's talk about everything!</h3>
            <p class="info-subtitle">
              Don't hesitate to reach out. I'm always open to discussing new projects, 
              creative ideas, or opportunities to be part of your vision.
            </p>

            <div class="contact-methods">
              <div class="contact-item" v-for="(method, idx) in contactMethods" :key="idx">
                <div class="contact-icon">
                  <i :class="method.icon"></i>
                </div>
                <div class="contact-details">
                  <h6 class="contact-label">{{ method.label }}</h6>
                  <a :href="method.link" class="contact-value">{{ method.value }}</a>
                </div>
              </div>
            </div>

            <div class="social-links">
              <h6 class="social-title">Follow Me</h6>
              <div class="social-icons">
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

        <!-- Contact Form -->
        <div class="col-lg-7" data-aos="fade-left">
          <form @submit="sendEmail" ref="contactForm" class="contact-form">
            <div class="form-floating mb-4">
              <input
                type="text"
                name="from_name"
                class="form-control"
                id="nameInput"
                placeholder="Your Name"
                required
              />
              <label for="nameInput">
                <i class="bi bi-person me-2"></i>Your Name
              </label>
            </div>

            <div class="form-floating mb-4">
              <input
                type="email"
                name="from_email"
                class="form-control"
                id="emailInput"
                placeholder="Your Email"
                required
              />
              <label for="emailInput">
                <i class="bi bi-envelope me-2"></i>Your Email
              </label>
            </div>

            <div class="form-floating mb-4">
              <textarea
                name="message"
                class="form-control"
                id="messageInput"
                placeholder="Your Message"
                style="height: 150px"
                required
              ></textarea>
              <label for="messageInput">
                <i class="bi bi-chat-dots me-2"></i>Your Message
              </label>
            </div>

            <button type="submit" class="btn btn-contact w-100" :disabled="loading">
              <span v-if="!loading" class="btn-content">
                <i class="bi bi-send-fill me-2"></i>
                Send Message
                <i class="bi bi-arrow-right ms-2"></i>
              </span>
              <span v-else class="btn-content">
                <span class="spinner-border spinner-border-sm me-2"></span>
                Sending...
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import emailjs from 'emailjs-com'
import Swal from 'sweetalert2'

const contactForm = ref(null)
const loading = ref(false)

const contactMethods = [
  {
    icon: 'bi bi-geo-alt-fill',
    label: 'Location',
    value: 'Philippines',
    link: '#'
  },
  {
    icon: 'bi bi-envelope-fill',
    label: 'Email',
    value: 'kimrynelellorico05@gmail.com',
    link: 'mailto:kimrynelellorico05@gmail.com'
  },
  {
    icon: 'bi bi-telephone-fill',
    label: 'Availability',
    value: 'Open for opportunities',
    link: '#'
  }
]

const socialLinks = [
  { name: 'GitHub', icon: 'bi bi-github', url: 'https://github.com/ElloricoDev' },
  { name: 'LinkedIn', icon: 'bi bi-linkedin', url: 'https://linkedin.com/in/kimrynelellorico' },
  { name: 'Email', icon: 'bi bi-envelope-at-fill', url: 'mailto:kimrynelellorico05@gmail.com' },
  { name: 'Facebook', icon: 'bi bi-facebook', url: '#' }
]

const sendEmail = (e) => {
  e.preventDefault()
  loading.value = true

  emailjs
    .sendForm(
      'service_ugzwumy',
      'template_fsfckjh',
      contactForm.value,
      'CZXkgTIJMlbET4JON'
    )
    .then(() => {
      Swal.fire({
        icon: 'success',
        title: 'Message Sent Successfully! 🎉',
        text: 'Thank you for reaching out! I\'ll get back to you as soon as possible.',
        confirmButtonColor: '#667eea',
        confirmButtonText: 'Great!',
        timer: 5000,
        timerProgressBar: true
      })
      contactForm.value.reset()
    })
    .catch((error) => {
      console.error('EmailJS Error:', error)
      Swal.fire({
        icon: 'error',
        title: 'Oops! Something went wrong',
        text: 'Failed to send your message. Please try again or contact me directly via email.',
        confirmButtonColor: '#dc3545',
        confirmButtonText: 'Okay'
      })
    })
    .finally(() => {
      loading.value = false
    })
}
</script>

<style scoped>
.contact-section {
  padding: 100px 0;
  background: linear-gradient(180deg, #ffffff 0%, #f8f9fa 100%);
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

.contact-info-wrapper {
  background: white;
  padding: 3rem;
  border-radius: 25px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
  height: 100%;
}

.info-title {
  font-size: 2rem;
  font-weight: 800;
  color: #1b263b;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.info-subtitle {
  color: #6c757d;
  line-height: 1.8;
  margin-bottom: 2.5rem;
}

.contact-methods {
  margin-bottom: 2.5rem;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding: 1.5rem;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.05), rgba(118, 75, 162, 0.05));
  border-radius: 15px;
  margin-bottom: 1rem;
  transition: all 0.3s ease;
}

.contact-item:hover {
  transform: translateX(5px);
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
}

.contact-icon {
  width: 55px;
  height: 55px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  border-radius: 13px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  color: white;
  flex-shrink: 0;
}

.contact-details {
  flex: 1;
}

.contact-label {
  font-size: 0.85rem;
  color: #6c757d;
  font-weight: 600;
  margin-bottom: 0.25rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.contact-value {
  font-size: 1.05rem;
  color: #1b263b;
  font-weight: 600;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-value:hover {
  color: #667eea;
}

.social-links {
  padding-top: 2rem;
  border-top: 2px solid #f1f3f5;
}

.social-title {
  font-weight: 700;
  color: #1b263b;
  margin-bottom: 1.5rem;
  font-size: 1.1rem;
}

.social-icons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.social-link {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.3rem;
  color: #667eea;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
}

.contact-form {
  background: white;
  padding: 3rem;
  border-radius: 25px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
}

.form-control {
  border: 2px solid #f1f3f5;
  border-radius: 15px;
  padding: 1.25rem 1.5rem;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.form-control:focus {
  border-color: #667eea;
  box-shadow: 0 0 0 0.25rem rgba(102, 126, 234, 0.15);
}

.form-floating > label {
  padding: 1.25rem 1.5rem;
  color: #6c757d;
}

.form-floating > .form-control:focus ~ label,
.form-floating > .form-control:not(:placeholder-shown) ~ label {
  color: #667eea;
}

.btn-contact {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 1.25rem 2rem;
  border-radius: 15px;
  font-weight: 600;
  font-size: 1.1rem;
  border: none;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
}

.btn-contact:hover:not(:disabled) {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
}

.btn-contact:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.btn-content {
  display: flex;
  align-items: center;
  justify-content: center;
}

.spinner-border {
  width: 1.2rem;
  height: 1.2rem;
}

@media (max-width: 991px) {
  .contact-info-wrapper {
    padding: 2rem;
    margin-bottom: 2rem;
  }

  .contact-form {
    padding: 2rem;
  }

  .info-title {
    font-size: 1.75rem;
  }
}

@media (max-width: 576px) {
  .contact-info-wrapper,
  .contact-form {
    padding: 1.5rem;
  }

  .contact-item {
    padding: 1rem;
  }

  .contact-icon {
    width: 45px;
    height: 45px;
    font-size: 1.25rem;
  }
}
</style>