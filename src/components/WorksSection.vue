<template>
  <section class="works">
    <div class="container">
      <!-- Header -->
      <div class="works-header">
        <h2>Most Loved Ads </h2>
        <!-- <button class="view-btn">VIEW ALL</button> -->
      </div>

      <!-- Grid -->
      <div class="works-grid">
        <div class="work-card" v-for="work in works" :key="work.title" @click="openVideo(work.video)">
          <!-- Image -->
          <div class="image-wrap">
            <img :src="work.image" alt="work image" />

            <!-- PLAY ICON -->
            <div class="play-overlay">
              <span class="play-btn">▶</span>
            </div>

            <div class="image-gradient"></div>
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
  <!-- VIDEO MODAL -->
  <div v-if="showVideo" class="video-modal" @click.self="closeVideo">
    <div class="video-box">
      <button class="close-btn" @click="closeVideo">✕</button>

      <iframe :src="`https://www.youtube.com/embed/${currentVideo}?autoplay=1`" title="YouTube video player"
        frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>
  </div>

</template>

<script setup>
import { ref } from 'vue'
import work1 from '../assets/images/services/ads3.PNG'
import work2 from '../assets/images/services/ads4.PNG'
import work3 from '../assets/images/services/ads5.PNG'
import work4 from '../assets/images/services/work4.png'

/* video modal state */
const showVideo = ref(false)
const currentVideo = ref(null)

/* open modal */
const openVideo = (id) => {
  currentVideo.value = id
  showVideo.value = true
}

/* close modal */
const closeVideo = () => {
  showVideo.value = false
  currentVideo.value = null
}

/* works data */
const works = [
  {
    title: 'PRODUCT AD – SMART FITNESS BOTTLE',
    image: work1,
    rate: 60,
    rank: 1,
    video: '0QGCXk5s1CY'
  },
  {
    title: 'REAL ESTATE – LUXURY APARTMENT',
    image: work2,
    rate: 74,
    rank: 2,
    video: 'B-MppfBEZus'
  },
  {
    title: 'PRODUCT AD – COSMETIC BRAND',
    image: work3,
    rate: 82,
    rank: 3,
    video: 'kBBgm1cRBqk'
  },
  {
    title: 'REAL ESTATE – VILLA PROMOTION',
    image: work4,
    rate: 68,
    rank: 4,
    video: 'Ra2R0MB0YUs'
  }
]
</script>

<style scoped>
/* ===== SECTION ===== */
.works {
  background: #dff5ff;
  padding: 20px 0;
}

/* ===== CONTAINER ===== */
.container {
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

/* ===== SECTION ===== */
.works {
  background: linear-gradient(180deg, #eaf6ff, #dff5ff);
  padding: 40px 0;
}

/* ===== HEADER ===== */
.works-header h2 {
  font-size: 44px;
  font-weight: 800;
  letter-spacing: .3px;
}

.view-btn {
  background: #0b3cff;
  color: #fff;
  border: none;
  padding: 12px 22px;
  border-radius: 30px;
  font-size: 14px;
  font-weight: 600;
  transition: .25s;
}

.view-btn:hover {
  background: #0626a8;
  transform: translateY(-2px);
}

/* ===== GRID ===== */
.works-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 36px;
}

/* ===== CARD ===== */
.work-card {
  position: relative;
  background: #fff;
  border-radius: 22px;
  overflow: hidden;
  transition: .35s ease;
  box-shadow: 0 8px 24px rgba(0, 0, 0, .06);
}

.work-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 25px 70px rgba(0, 0, 0, .18);
}

/* ===== IMAGE ===== */
.image-wrap {
  position: relative;
  overflow: hidden;
}

.image-wrap img {
  width: 100%;
  height: 300px;
  object-fit: cover;
  transition: .6s ease;
}

/* zoom effect */
.work-card:hover .image-wrap img {
  transform: scale(1.08);
  filter: brightness(.75);
}

/* gradient bottom */
.image-gradient {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 120px;
  background: linear-gradient(transparent, rgba(0, 0, 0, .9));
  pointer-events: none;
}

/* PLAY BUTTON */
.play-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: .35s;
}

.play-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: rgba(255, 255, 255, .95);
  color: #0b3cff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 26px;
  font-weight: bold;
  box-shadow: 0 10px 30px rgba(0, 0, 0, .3);
  transform: scale(.7);
  transition: .35s;
}

.work-card:hover .play-overlay {
  opacity: 1;
}

.work-card:hover .play-btn {
  transform: scale(1);
}

/* ===== CONTENT ===== */
.work-content {
  padding: 22px;
}

.work-content h4 {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 18px;
  line-height: 1.4;
}

/* ===== STATS ===== */
.stats {
  display: flex;
  gap: 14px;
}

.stat {
  flex: 1;
  background: linear-gradient(180deg, #f3f8ff, #eef4ff);
  border-radius: 16px;
  padding: 6px 16px;
  text-align: center;
  transition: .3s;
}

.work-card:hover .stat {
  background: linear-gradient(180deg, #5a73d6, #0626a8);
}

.stat .value {
  display: block;
  font-size: 15px;
  font-weight: 800;
  color: #516edf;
  transition: .3s;
}

.work-card:hover .stat .value {
  color: #fff;
}

.stat .label {
  font-size: 12px;
  color: #555;
  transition: .3s;
}

.work-card:hover .stat .label {
  color: #cfe0ff;
}

/* ===== MOBILE ===== */
@media(max-width:900px) {
  .works-grid {
    grid-template-columns: 1fr;
  }

  .image-wrap img {
    height: 230px;
  }

  .works {
    padding: 60px 0;
  }

  .works-header h2 {
    font-size: 32px;
  }
}

/* VIDEO MODAL */
.video-modal {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, .75);
  backdrop-filter: blur(6px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  animation: fadeIn .25s ease;
}

.video-box {
  position: relative;
  width: 90%;
  max-width: 900px;
  aspect-ratio: 16/9;
  background: #000;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 30px 80px rgba(0, 0, 0, .6);
}

.video-box iframe {
  width: 100%;
  height: 100%;
}

/* CLOSE BUTTON */
.close-btn {
  position: absolute;
  top: -40px;
  right: 0;
  background: #fff;
  color: #000;
  border: none;
  width: 34px;
  height: 34px;
  border-radius: 50%;
  font-size: 16px;
  cursor: pointer;
  font-weight: bold;
  box-shadow: 0 10px 25px rgba(0, 0, 0, .5);
}

@keyframes fadeIn {
  from {
    opacity: 0
  }

  to {
    opacity: 1
  }
}
</style>
