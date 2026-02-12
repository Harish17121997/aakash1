<template>
  <section class="services">
    <div class="container">

      <!-- Header -->
      <div class="services-header">
        <h1>Explore Ads<br />by Categories</h1>
        <button class="view-btn" @click="toggleServices">
          {{ showAll ? 'SHOW LESS' : 'ALL SERVICES' }}
        </button>
      </div>

      <!-- Cards -->
      <div class="service-grid">
        <div
          class="service-card"
          v-for="service in displayedServices"
          :key="service.title"
          @click="openCategory(service.slug)"
        >
          <span class="arrow">↗</span>

          <div class="card-content">
            <h3>{{ service.title }}</h3>
            <p>{{ service.desc }}</p>
            <span class="tag">{{ service.tag }}</span>
          </div>

          <div class="card-image">
            <img :src="service.img" alt="service image" />
          </div>
        </div>
      </div>

    </div>

    <!-- ================= MODAL ================= -->
    <div v-if="activeCategory" class="category-modal" @click="closeModal">
      <div class="category-content" @click.stop>

        <div class="modal-header">
          <h2>{{ activeTitle }}</h2>
          <span class="close-btn" @click="closeModal">✕</span>
        </div>
        <p class="hint">Click any video to preview</p>
        <!-- video thumbnails -->
        <div class="video-list">
          <div
            class="video-item"
            v-for="video in activeVideos"
            :key="video.id"
            @click="playVideo(video.id)"
          >
            <img :src="`https://img.youtube.com/vi/${video.id}/hqdefault.jpg`">
            <p>{{ video.title }}</p>
          </div>
        </div>

        <!-- player -->
        <div v-if="playingVideo" class="player-wrapper">
          <iframe
            :src="`https://www.youtube.com/embed/${playingVideo}?autoplay=1&rel=0`"
            frameborder="0"
            allow="autoplay; encrypted-media"
            allowfullscreen>
          </iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

import service1 from '../assets/images/services/product01.png'
import service2 from '../assets/images/services/realestate01.png'
import service3 from '../assets/images/services/services3.png'

/* ---------------- SERVICES ---------------- */

const allServices = [
  { title:'PRODUCT ADS', slug:'product', desc:'High converting short-form product videos for brands', tag:'Short Form', img:service1 },
  { title:'REAL ESTATE ADS', slug:'realestate', desc:'Luxury & lifestyle real estate promotional videos', tag:'Lifestyle', img:service2 },
  { title:'TV COMMERCIALS', slug:'tvc', desc:'Professional brand commercials for mass audience', tag:'Broadcast', img:service3 },
  { title:'PERFORMANCE MARKETING ADS', slug:'performance', desc:'ROI driven paid ads campaigns', tag:'Paid Ads', img:service1 },
  { title:'EVENT ADS', slug:'event', desc:'Event promotions and launch videos', tag:'Promotion', img:service2 },
  { title:'AI ADS', slug:'ai', desc:'AI generated creatives & avatars', tag:'AI Creative', img:service3 }
]

/* first 3 visible */
const showAll = ref(false)

const displayedServices = computed(()=>{
  return showAll.value ? allServices : allServices.slice(0,3)
})

const toggleServices = () => {
  showAll.value = !showAll.value
}

/* ---------------- VIDEO DATABASE ---------------- */

const videoDB = {
  product:[
    {title:'Cosmetic Ad', id:'kBBgm1cRBqk'},
    {title:'Fitness', id:'0QGCXk5s1CY'},
    {title:'Fitness', id:'AVsb7tRmfXA'},
  ],
  realestate:[
    {title:'', id:'k9JhTISwU4Q'},
    {title:'', id:'OIeGmQbNXcE'}, 
    {title:'', id:'B-MppfBEZus'}, 
    {title:'', id:'5J7lG7C5o68'}, 
    {title:'', id:'dxZZ59cm9fI'}, 
    {title:'', id:'3k7ztBCR63k'},  
    {title:'', id:'qAAqObAi9I4'},  
  ],
  tvc:[
    {title:'Retail Brand TVC', id:'9EICU8E73_A'}
  ],
  performance:[
    {title:'Meta Ads Campaign', id:'aegmFAWAcRk'}
  ],
  event:[
    {title:'Wedding Highlight', id:'BdhCW0VFMMA'}
  ],
  ai:[
    {title:'AI Avatar Ad', id:'5y6R7LMUIQ0'}
  ]
}

/* ---------------- MODAL LOGIC ---------------- */

const activeCategory = ref(null)
const activeVideos = ref([])
const activeTitle = ref('')
const playingVideo = ref(null)

const openCategory = (slug)=>{
  activeCategory.value = slug
  activeVideos.value = videoDB[slug]
  playingVideo.value = null

  const found = allServices.find(s=>s.slug===slug)
  activeTitle.value = found.title

  document.body.style.overflow = 'hidden'
}

const closeModal = ()=>{
  activeCategory.value = null
  playingVideo.value = null
  document.body.style.overflow = ''
}

const playVideo = (id)=>{
  playingVideo.value = id
}
</script>

<style scoped>

/* SECTION */
.services{
  background:url('../assets/images/services/services-bg.png');
  background-size:cover;
  background-position:center;
  padding:20px 0;
}

.container{
  max-width:1200px;
  margin:auto;
  padding:0 24px;
}

/* HEADER */
.services-header{
  display:flex;
  justify-content:space-between;
  margin-bottom:40px;
}

.services-header h1{
  font-size:52px;
  font-weight:800;
}

.view-btn{
  background:#0b3cff;
  color:#fff;
  border:none;
  padding:10px 18px;
  border-radius:6px;
  cursor:pointer;
  height: 40px;
}

/* GRID */
.service-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:24px;
}

/* CARD */
.service-card{
  background:#111;
  color:#fff;
  padding:28px;
  border-radius:20px;
  min-height:360px;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  position:relative;
  cursor:pointer;
  transition:.3s;
}

.service-card:hover{
  transform:translateY(-6px);
}

.card-content h3{
  font-size:18px;
  font-weight:700;
  margin-bottom:10px;
}

.card-content p{
  font-size:14px;
  color:#cfcfcf;
  margin-bottom:14px;
}

.tag{
  background:#222;
  padding:6px 12px;
  border-radius:20px;
  font-size:12px;
  color:#a6ff00;
}

/* IMAGE AREA — LOCKED RATIO */
.card-image{
  position:relative;
  width:100%;
  height:240px;
  border-radius:14px;
  overflow:hidden;
  margin-top:18px;
  background:linear-gradient(145deg,#0f1117,#05060a);
  display:flex;
  align-items:center;
  justify-content:center;
}

.card-image img{
  position:absolute;
  inset:0;
  width:100%;
  height:100%;
  object-fit:cover;      /* important */
  object-position:center;
}

hover animation
.service-card:hover .card-image img{
  transform:scale(1.08);
}

.arrow{
  position:absolute;
  top:20px;
  right:20px;
  background:#a6ff00;
  color:#000;
  width:36px;
  height:36px;
  border-radius:50%;
  display:grid;
  place-items:center;
}

/* ================= MODAL ================= */

/* ===== IMPROVED MODAL LAYER ===== */

.category-modal{
  position:fixed;
  inset:0;
  background:linear-gradient(
    180deg,
    rgba(2,6,23,0.85),
    rgba(2,6,23,0.95)
  );
  backdrop-filter: blur(12px);
  display:flex;
  justify-content:center;
  align-items:center;
  z-index:9999;
  padding:40px 20px;
  animation:fadeIn .25s ease;
}

@keyframes fadeIn{
  from{opacity:0}
  to{opacity:1}
}

.category-content{
  width:100%;
  max-width:1200px;
  background:linear-gradient(180deg,#374d8c,#222b4d);
  border-radius:22px;
  padding:32px;
  max-height:90vh;
  overflow-y:auto;
  border:1px solid rgba(255,255,255,.08);
  box-shadow:0 30px 80px rgba(0,0,0,.6);
  scrollbar-width: thin;
}

/* ================================
   CATEGORY MODAL (GLASS EFFECT)
================================ */

.category-modal{
  position:fixed;
  inset:0;
  background:linear-gradient(180deg,rgba(2,6,23,.85),rgba(2,6,23,.96));
  backdrop-filter:blur(12px);
  display:flex;
  justify-content:center;
  align-items:center;
  z-index:9999;
  padding:40px 20px;
  animation:fadeIn .25s ease;
}

@keyframes fadeIn{
  from{opacity:0}
  to{opacity:1}
}

.category-content{
  width:100%;
  max-width:1200px;
  background:linear-gradient(180deg,#5b75bd,#222b4d);
  border-radius:22px;
  padding:32px;
  max-height:90vh;
  overflow-y:auto;
  border:1px solid rgba(255,255,255,.08);
  box-shadow:0 30px 80px rgba(0,0,0,.65);
}


/* ================================
   MODAL HEADER
================================ */

.modal-header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:26px;
  padding-bottom:14px;
  border-bottom:1px solid rgba(255,255,255,.08);
}

.modal-header h2{
  font-size:26px;
  font-weight:700;
  letter-spacing:.5px;
}

.close-btn{
  width:36px;
  height:36px;
  border-radius:50%;
  display:grid;
  place-items:center;
  background:#141826;
  color:white;
  font-size:18px;
  cursor:pointer;
  transition:.25s;
}

.close-btn:hover{
  background:#0b3cff;
  transform:rotate(90deg);
}


/* ================================
   VIDEO GRID
================================ */

.video-list{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:24px;
}

.hint{
  margin-bottom:18px;
  color:#f7f7f7;
  font-size:14px;
}


/* ================================
   VIDEO CARDS
================================ */

.video-item{
  position:relative;
  border-radius:16px;
  overflow:hidden;
  cursor:pointer;
  transition:.35s;
  background:#000;
}

.video-item img{
  width:100%;
  height:180px;
  object-fit:cover;
  transition:.5s;
}

/* zoom + darken on hover */
.video-item:hover img{
  transform:scale(1.08);
  filter:brightness(.7);
}

/* PLAY BUTTON */
.video-item::after{
  content:'▶';
  position:absolute;
  inset:0;
  display:grid;
  place-items:center;
  font-size:44px;
  color:white;
  opacity:0;
  transition:.3s;
}

.video-item:hover::after{
  opacity:1;
}

/* title overlay */
.video-item p{
  position:absolute;
  bottom:0;
  left:0;
  right:0;
  margin:0;
  padding:12px 14px;
  font-size:14px;
  font-weight:600;
  background:linear-gradient(transparent,rgba(0,0,0,.95));
  color: wheat;
}


/* ================================
   VIDEO PLAYER (CINEMA MODE)
================================ */

.player-wrapper{
  position:relative;
  margin-top:30px;
  width:100%;
  aspect-ratio:16/9;
  border-radius:16px;
  overflow:hidden;
  box-shadow:0 20px 60px rgba(0,0,0,.6);
  animation:playerIn .3s ease;
}

@keyframes playerIn{
  from{transform:scale(.95);opacity:0}
  to{transform:scale(1);opacity:1}
}

.player-wrapper iframe{
  width:100%;
  height:100%;
  border:none;
}


/* ================================
   MOBILE RESPONSIVE
================================ */

@media(max-width:768px){

  .category-content{
    padding:20px;
  }

  .video-item img{
    height:150px;
  }

  .modal-header h2{
    font-size:20px;
  }
  .services-header h1{
    font-size: 28px;
  }

}

</style>
