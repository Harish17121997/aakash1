<template>
  <section class="services">
    <div class="container">
      <!-- Section Header -->
      <div class="services-header">
        <h1>OUR<br />SERVICES</h1>
        <button class="view-btn" @click="">ALL SERVICES</button>
      </div>

      <!-- Cards -->
      <div class="service-grid">
        <div
          class="service-card"
          v-for="service in services"
          :key="service.title"
        >
          <span class="arrow">↗</span>

          <!-- Text Content -->
          <div class="card-content">
            <h3>{{ service.title }}</h3>
            <p>{{ service.desc }}</p>
            <span class="tag">{{ service.tag }}</span>
          </div>

          <!-- Image -->
          <div class="card-image">
            <img :src="service.img" alt="service image" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import service1 from '../assets/images/services/services1.png'
import service2 from '../assets/images/services/services2.png'
import service3 from '../assets/images/services/services3.png'

const services = [
  {
    title: 'PRODUCT ADS',
    desc: 'High converting short-form product videos for brands',
    tag: 'Short Form',
    img: service1
  },
  {
    title: 'REAL ESTATE ADS',
    desc: 'Luxury & lifestyle real estate promotional videos',
    tag: 'Lifestyle',
    img: service2
  },
  {
    title: 'TV COMMERCIALS',
    desc: 'Professional brand commercials for mass audience',
    tag: 'Broadcast',
    img: service3
  },
]
</script>

<style scoped>
/* ===== SECTION ===== */
.services {
  background: url('../assets/images/services/services-bg.png');
  background-size: cover;
  background-position: center;
  padding: 100px 0;
}

/* ===== CONTAINER ===== */
.container {
  max-width: 1200px;
  margin: auto;
  padding: 0 24px;
}

/* ===== HEADER ===== */
.services-header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 48px;
}

.services-header h2 {
  font-size: 42px;
  font-weight: 800;
  line-height: 1.1;
  margin: 0;
}

.view-btn {
  background: #0b3cff;
  color: #fff;
  border: none;
  padding: 10px 18px;
  border-radius: 6px;
  font-size: 14px;
  cursor: pointer;
}

/* ===== GRID ===== */
.service-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

/* ===== CARD ===== */
.service-card {
  background: #111;
  color: #ffffff;
  padding: 28px;
  border-radius: 20px;
  position: relative;
  min-height: 320px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: transform 0.3s ease;
}

.service-card:hover {
  transform: translateY(-6px);
}

/* ===== CONTENT ===== */
.card-content h3 {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 10px;
}

.card-content p {
  font-size: 14px;
  color: #cfcfcf;
  line-height: 1.5;
  margin-bottom: 14px;
}

.tag {
  display: inline-block;
  background: #222;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 12px;
  color: #a6ff00;
}

/* ===== IMAGE ===== */
.card-image {
  margin-top: 20px;
  text-align: right;
}

.card-image img {
  height: auto;
}

/* ===== ARROW ===== */
.arrow {
  position: absolute;
  top: 20px;
  right: 20px;
  background: #a6ff00;
  color: #000;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  font-weight: 700;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 900px) {
  .service-grid {
    grid-template-columns: 1fr;
  }

  .services-header {
    flex-direction: column;
    gap: 20px;
  }

  .services-header h2 {
    font-size: 34px;
  }

  .card-image {
    text-align: center;
  }
}
</style>
