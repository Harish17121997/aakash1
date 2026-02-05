<template>
  <section class="works">
    <div class="container">
      <!-- Header -->
      <div class="works-header">
        <h2>OUR<br />WORKS</h2>
        <button class="view-btn">VIEW ALL</button>
      </div>

      <!-- Grid -->
      <div class="works-grid">
        <div class="work-card" v-for="work in works" :key="work.title">
          <!-- Image -->
          <div class="image-wrap">
            <img :src="work.image" alt="work image" />
          </div>

          <!-- Content -->
          <div class="work-content">
            <h4>{{ work.title }}</h4>

            <div class="stats">
              <div class="stat">
                <span class="value">{{ work.rate }}%</span>
                <span class="label">Conversion</span>
              </div>

              <div class="stat">
                <span class="value">#{{ work.rank }}</span>
                <span class="label">Rank</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import work1 from '../assets/images/services/work1.png'
import work2 from '../assets/images/services/work2.png'
 
const works = [
  {
    title: 'PRODUCT AD – SMART FITNESS BOTTLE',
    image: work1,
    rate: 60,
    rank: 1
  },
  {
    title: 'REAL ESTATE – LUXURY APARTMENT',
    image: work2,
    rate: 60,
    rank: 1
  },
  {
    title: 'PRODUCT AD – SMART FITNESS BOTTLE',
    image: work1,
    rate: 60,
    rank: 1
  },
  {
    title: 'REAL ESTATE – LUXURY APARTMENT',
    image: work2,
    rate: 60,
    rank: 1
  }
]
</script>

<style scoped>
/* ===== SECTION ===== */
.works {
  background: #dff5ff;
  padding: 100px 0;
}

/* ===== CONTAINER ===== */
.container {
  max-width: 1200px;
  margin: auto;
  padding: 0 24px;
}

/* ===== HEADER ===== */
.works-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 48px;
}

.works-header h2 {
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
.works-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px;
}

/* ===== CARD ===== */
.work-card {
  background: #ffffff;
  border-radius: 20px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.work-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.12);
}

/* ===== IMAGE ===== */
.image-wrap img {
  width: 100%;
  height: 260px;
  object-fit: cover;
}

/* ===== CONTENT ===== */
.work-content {
  padding: 20px;
}

.work-content h4 {
  font-size: 14px;
  font-weight: 700;
  margin-bottom: 16px;
  letter-spacing: 0.3px;
}

/* ===== STATS ===== */
.stats {
  display: flex;
  justify-content: space-between;
}

.stat {
  background: #f3f8ff;
  border-radius: 14px;
  padding: 10px 16px;
  text-align: center;
}

.stat .value {
  display: block;
  font-size: 18px;
  font-weight: 800;
  color: #0b3cff;
}

.stat .label {
  font-size: 12px;
  color: #555;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 900px) {
  .works-grid {
    grid-template-columns: 1fr;
  }

  .works-header {
    flex-direction: column;
    gap: 20px;
  }

  .works-header h2 {
    font-size: 34px;
  }
}
</style>
