```vue
<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const services = [
  {
    title: 'CONSTRUCTION',
    description: 'We specialize in all kinds of construction works. Our certified team provides the services in time and on the highest level.',
   image: '/images/image24.jpg'
  },
  {
    title: 'ABOUT US',
    description: 'BuildWall is completely client-oriented company. We are able to meet schedule deadlines with top quality.',
   image: '/images/image23.jpg'
  },
  {
    title: 'EFFECTIVE TEAMWORK',
    description: 'We have a very good team-based and team-work attitude, working together to find the best solutions.',
    image: '/images/image25.jpg'
  }
]

const projects = [
  { title: 'Modern House', category: 'BUILDING', image: '/images/ARCHITECTURE & BUILDING.webp' },
  { title: 'Office Building', category: 'OFFICE', image: '/images/BUILDING ENGINEERING.jpg' },
  { title: 'Interior Design', category: 'INTERIOR', image: '/images/INTERIOR DESIGN.jpg' },
  { title: 'New Residence', category: 'BUILDING', image: '/images/HOUSE RENOVATION.avif' },
  { title: 'Living Room', category: 'INTERIOR', image: '/images/image38.jpg' },
  { title: 'Luxury House', category: 'CONSULTING', image: '/images/PRECONSTRUCTION PLANNING.png' }
]

const selectedCategory = ref('ALL')

const filteredProjects = () => {
  if (selectedCategory.value === 'ALL') {
    return projects
  }

  return projects.filter(project => project.category === selectedCategory.value)
}
</script>

<template>
  <div>
    <!-- Contactgegevens -->
    <div class="topbar">
      <div class="container topbar-content">
        <span>BuildIcon - Construction Company</span>
        <span>Get in touch with our team</span>
      </div>
    </div>

    <!-- Header -->
    <header class="container header">
      <a href="#home" class="logo">
        <span class="logo-icon">▥</span>
        <span>Build<span class="orange">Icon</span>
          <small>CONSTRUCTION COMPANY</small>
        </span>
      </a>

      <div class="contact-info">
        <div>
          <span class="orange">▣</span>
          <p>CUSTOM SUPPORT & SALE<strong>+7-495-1234567</strong></p>
        </div>

        <div>
          <span class="orange">◷</span>
          <p>WORKING TIME<strong>MON–SAT: 08:00–18:00</strong></p>
        </div>

        <a class="quote-button" href="#contact">✉ REQUEST A QUOTE</a>
      </div>
    </header>

    <!-- Navigatie -->
    <nav class="navigation">
      <div class="container nav-content">
        <button class="menu-button" @click="menuOpen = !menuOpen">
          {{ menuOpen ? '✕' : '☰' }} MENU
        </button>

        <ul :class="{ 'menu-open': menuOpen }">
          <li><a class="active" href="#home" @click="menuOpen = false">HOME</a></li>
          <li><a href="#about" @click="menuOpen = false">ABOUT</a></li>
          <li><a href="#services" @click="menuOpen = false">SERVICES⌄</a></li>
          <li><a href="#projects" @click="menuOpen = false">PROJECTS⌄</a></li>
          <li><a href="#news" @click="menuOpen = false">NEWS</a></li>
          <li><a href="#contact" @click="menuOpen = false">CONTACT</a></li>
        </ul>

        <a class="search" href="#projects" aria-label="Zoek projecten">⌕</a>
      </div>
    </nav>

    <!-- Grote afbeelding -->
    <main>
      <section class="hero" id="home">
        <div class="container hero-content">
          <div class="hero-text">
            <span class="small-line"></span>
            <p class="eyebrow">HIGH QUALITY GUARANTEED</p>
            <h1>Constructing<br>Is Our Life Business</h1>
            <div class="hero-buttons">
              <a href="#services" class="button yellow-button">OUR SERVICES ›</a>
              <a href="#about" class="button dark-button">ABOUT US ›</a>
            </div>
          </div>
        </div>
      </section>

      <!-- Korte introductie -->
      <section class="container intro" id="about">
        <h2>We Are BuildWall</h2>
        <p>We have been transforming ideas and visions into award-winning projects.</p>
        <a href="#contact" class="button yellow-button">✉ REQUEST A QUOTE</a>
      </section>

      <!-- Diensten -->
      <section class="services-section" id="services">
        <div class="container">
          <h2 class="section-title">Who we are</h2>

          <div class="services-grid">
            <article class="service-card" v-for="service in services" :key="service.title">
              <img :src="service.image" :alt="service.title">
              <div class="service-info">
                <h3>{{ service.title }}</h3>
                <span class="small-line"></span>
                <p>{{ service.description }}</p>
                <a href="#contact" class="button yellow-button">LEARN MORE ›</a>
              </div>
            </article>
          </div>
        </div>
      </section>

      <!-- Projecten -->
      <section class="container projects-section" id="projects">
        <h2 class="section-title">Featured Projects</h2>

        <div class="filters">
          <button
            v-for="category in ['ALL', 'BUILDING', 'CONSULTING', 'INTERIOR', 'OFFICE']"
            :key="category"
            :class="{ chosen: selectedCategory === category }"
            @click="selectedCategory = category"
          >
            {{ category }}
          </button>
        </div>

        <div class="projects-grid">
          <article class="project-card" v-for="project in filteredProjects()" :key="project.title">
            <img :src="project.image" :alt="project.title">
            <div class="project-overlay">
              <h3>{{ project.title }}</h3>
              <p>{{ project.category }}</p>
              <a href="#contact">LEARN MORE ›</a>
            </div>
          </article>
        </div>
      </section>

      <!-- Contact -->
      <section class="contact-section" id="contact">
        <div class="container contact-content">
          <div>
            <h2>Ready to start your project?</h2>
            <p>Contact our team to discuss your construction plans.</p>
          </div>
          <a href="mailto:info@buildicon.com" class="button yellow-button">CONTACT US ›</a>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer id="news">
      <div class="container footer-content">
        <a href="#home" class="logo footer-logo">
          <span class="logo-icon">▥</span>
          <span>Build<span class="orange">Icon</span>
            <small>CONSTRUCTION COMPANY</small>
          </span>
        </a>
        <p>Building better spaces for the future.</p>
        <a href="#home">Back to top ↑</a>
      </div>
    </footer>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  color: #252b32;
  font-family: Arial, sans-serif;
}

a {
  color: inherit;
  text-decoration: none;
}

button {
  font: inherit;
}

.container {
 width: 100%;
max-width: 1170px;
  margin: 0 auto;
}

.orange {
  color: #ffb526;
}

/* Bovenste balk */
.topbar {
  background: #293748;
  color: white;
  padding: 14px 0;
  font-size: 13px;
}

.topbar-content {
  display: flex;
  justify-content: space-between;
  gap: 15px;
}

/* Header */
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
  padding-top: 22px;
  padding-bottom: 22px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 28px;
  font-weight: bold;
  white-space: nowrap;
}

.logo-icon {
  color: #ffb526;
  font-size: 44px;
}

.logo small {
  display: block;
  font-size: 9px;
  letter-spacing: 1px;
}

.contact-info {
  display: flex;
  align-items: center;
  gap: 25px;
}

.contact-info > div {
  display: flex;
  align-items: center;
  gap: 10px;
}

.contact-info > div > span {
  font-size: 27px;
}

.contact-info p {
  margin: 0;
  color: #777;
  font-size: 11px;
}

.contact-info strong {
  display: block;
  margin-top: 5px;
  color: #252b32;
  font-size: 13px;
}

.quote-button {
  background: #252b32;
  color: white;
  padding: 17px 20px;
  font-size: 12px;
  font-weight: bold;
}

/* Navigatie */
.navigation {
  position: relative;
  z-index: 2;
  background: #ffb526;
}

.nav-content,
.navigation ul {
  display: flex;
  align-items: center;
}

.nav-content {
  justify-content: space-between;
}

.navigation ul {
  gap: 0;
  margin: 0;
  padding: 0;
  list-style: none;
}

.navigation li a {
  display: block;
  padding: 20px 17px;
  color: white;
  font-size: 12px;
  font-weight: bold;
}

.navigation li a:hover,
.navigation li a.active {
  background: #252b32;
}

.search {
  padding: 10px;
  color: white;
  font-size: 27px;
}

.menu-button {
  display: none;
}

/* Hero */
.hero {
  min-height: 520px;
  background:
    linear-gradient(90deg, rgba(255,255,255,.85), rgba(255,255,255,.08)),
      url('/images/image17.jpg') center / cover no-repeat;
  }

.hero-content {
  display: flex;
  align-items: center;
  min-height: 520px;
}

.hero-text {
  max-width: 600px;
}

.small-line {
  display: block;
  width: 24px;
  height: 3px;
  margin-bottom: 15px;
  background: #ffb526;
}

.eyebrow {
  font-size: 15px;
  font-weight: bold;
}

.hero h1 {
  margin: 20px 0 30px;
  font-size: clamp(38px, 5vw, 58px);
  line-height: 1.25;
}

.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.button {
  display: inline-block;
  padding: 16px 24px;
  font-size: 12px;
  font-weight: bold;
}

.yellow-button {
  background: #ffb526;
  color: white;
}

.dark-button {
  background: #252b32;
  color: white;
}

.button:hover,
.quote-button:hover {
  opacity: .85;
}

/* Intro */
.intro {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  padding-top: 30px;
  padding-bottom: 30px;
}

.intro h2 {
  color: #ffb526;
}

.intro p {
  font-size: 13px;
}

/* Diensten */
.services-section {
  padding: 45px 0 60px;
  background: #f5f5f5;
}

.section-title {
  margin: 0 0 25px;
  font-size: 27px;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 25px;
}

.service-card {
  background: white;
  box-shadow: 0 2px 10px #0000000a;
}

.service-card img {
  display: block;
  width: 100%;
  height: 190px;
  object-fit: cover;
}

.service-info {
  padding: 22px;
}

.service-info h3 {
  font-size: 18px;
}

.service-info p {
  min-height: 75px;
  color: #68717a;
  font-size: 13px;
  line-height: 1.7;
}

.service-info .button {
  padding: 12px 17px;
}

/* Projecten */
.projects-section {
  padding-top: 50px;
  padding-bottom: 60px;
}

.filters {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 22px;
  margin-bottom: 25px;
}

.filters button {
  border: 0;
  background: transparent;
  cursor: pointer;
  color: #68717a;
  font-size: 12px;
}

.filters button:hover,
.filters button.chosen {
  color: #ffb526;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.project-card {
  position: relative;
  min-height: 230px;
  overflow: hidden;
  background: #ddd;
}

.project-card img {
  display: block;
  width: 100%;
  height: 100%;
  min-height: 230px;
  object-fit: cover;
  transition: transform .3s;
}

.project-card:hover img {
  transform: scale(1.06);
}

.project-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 25px;
  background: #202a35e8;
  color: white;
  opacity: 0;
  transition: opacity .3s;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-overlay a {
  color: #ffb526;
  font-size: 12px;
  font-weight: bold;
}

/* Contact */
.contact-section {
  padding: 45px 0;
  background: #252b32;
  color: white;
}

.contact-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 25px;
}

.contact-content h2 {
  margin-top: 0;
}

.contact-content p {
  color: #ddd;
}

/* Footer */
footer {
  padding: 35px 0;
  background: #1d2228;
  color: white;
}

.footer-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

.footer-logo {
  font-size: 23px;
}

.footer-logo .logo-icon {
  font-size: 35px;
}

/* Tablet */
@media (max-width: 900px) {
  .header {
    align-items: flex-start;
    flex-direction: column;
  }

  .contact-info {
    width: 100%;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .navigation li a {
    padding: 17px 12px;
  }

  .hero,
  .hero-content {
    min-height: 440px;
  }

  .services-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .projects-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .intro {
    flex-wrap: wrap;
  }
}

/* Mobiel */
@media (max-width: 600px) {
  .topbar-content {
    flex-direction: column;
    gap: 5px;
  }

  .contact-info {
    align-items: flex-start;
    flex-direction: column;
  }

  .quote-button {
    display: inline-block;
  }

  .nav-content {
    min-height: 55px;
    flex-wrap: wrap;
  }

  .menu-button {
    display: block;
    padding: 17px 0;
    border: 0;
    background: transparent;
    color: white;
    cursor: pointer;
    font-weight: bold;
  }

  .navigation ul {
    display: none;
    width: 100%;
    align-items: stretch;
    flex-direction: column;
  }

  .navigation ul.menu-open {
    display: flex;
  }

  .navigation li a {
    padding: 15px;
  }

  .search {
    margin-left: auto;
  }

  .hero,
  .hero-content {
    min-height: 400px;
  }

  .hero {
    background-position: 60% center;
  }

  .hero h1 {
    font-size: 38px;
  }

  .intro {
    align-items: flex-start;
    flex-direction: column;
  }

  .services-grid,
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .service-card img {
    height: 220px;
  }

  .project-card {
    min-height: 250px;
  }

  .project-card img {
    min-height: 250px;
  }

  .contact-content,
  .footer-content {
    align-items: flex-start;
    flex-direction: column;
  }
}
</style>
```