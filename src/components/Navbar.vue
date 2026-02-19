<template>
  <nav class="navbar">
    <div class="container nav-inner">

      <!-- LEFT : LOGO -->
      <div class="nav-left">
        <img class="logo-img" :src="logo" alt="Pebble Media Logo" />
      </div>

      <!-- CENTER : NAV LINKS -->
      <ul class="nav-links">
        <li @click="goServices">Services</li>
        <li @click="goUsecases">Use Cases</li>
        <li @click="goResources">Resources</li>
        <li @click="goPricing">About</li>
      </ul>

      <!-- RIGHT : CTA + MOBILE -->
      <div class="nav-right">
        <button class="cta-btn" @click="$emit('open-contact')">Get in Touch</button>

        <button
          class="menu-btn"
          @click="toggleMenu"
          aria-label="Toggle Menu"
        >
          ☰
        </button>
      </div>

    </div>

    <!-- MOBILE OVERLAY MENU -->
    <transition name="menu">
      <div v-if="isOpen" class="mobile-overlay">

        <div class="mobile-menu">
          <span @click="goServices">Services</span>
          <span @click="goUsecases">Use Cases</span>
          <span @click="goResources">Resources</span>
          <span @click="goPricing">Pricing</span>

          <button class="mobile-cta" @click="$emit('open-contact')">Get in Touch</button>
        </div>


      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import logo from '@/assets/images/Navbar/Logo2.png'
const emit = defineEmits([
  'go-services',
  'go-usecases',
  'go-resources',
  'go-pricing',
  'open-contact'
])

const isOpen = ref(false)
const toggleMenu = () => (isOpen.value = !isOpen.value)
const goServices = () => {
  emit('go-services')
  isOpen.value = false   // close mobile menu also
}

const goUsecases = () => {
  emit('go-usecases')
  isOpen.value = false
}

const goResources = () => {
  emit('go-resources')
  isOpen.value = false
}

const goPricing = () => {
  emit('go-pricing')
  isOpen.value = false
}

</script>


<style scoped>

/* ===== NAVBAR BASE ===== */
.navbar{
  background:#4577f5;
  position:sticky;
  top:0;
  z-index:999;
  box-shadow:0 6px 20px rgba(0,0,0,0.20);
}

/* CONTAINER */
.container{
  max-width:1320px;
  margin:auto;
  padding:0 24px;
}

/* GRID LAYOUT */
.nav-inner{
  height:78px;
  display:grid;
  grid-template-columns:auto 1fr auto;
  align-items:center;
}

/* LOGO */
.logo-img{
  height:30px;
  width:auto;
  object-fit:contain;
  display:block;
}

/* NAV LINKS */
.nav-links{
  display:flex;
  justify-content:center;
  gap:40px;
  list-style:none;
  padding:0;
  margin:0;
}

.nav-links li{
  color:white;
  font-size:14px;
  font-weight:500;
  cursor:pointer;
  position:relative;
  transition:.25s;
}

/* FIGMA STYLE HOVER LINE */
.nav-links li::after{
  content:'';
  position:absolute;
  left:50%;
  bottom:-8px;
  width:0;
  height:2px;
  background:#A6FF00;
  transform:translateX(-50%);
  transition:.3s ease;
}

.nav-links li:hover::after{
  width:100%;
}

.nav-links li:hover{
  opacity:.8;
}

/* RIGHT SIDE */
.nav-right{
  display:flex;
  align-items:center;
  gap:16px;
}

/* CTA BUTTON */
.cta-btn{
  background:white;
  color:#0039C8;
  border:none;
  padding:10px 20px;
  border-radius:22px;
  font-weight:600;
  cursor:pointer;
  transition:.25s;
}

.cta-btn:hover{
  transform:translateY(-2px);
  box-shadow:0 8px 18px rgba(0,0,0,0.25);
}

/* HAMBURGER */
.menu-btn{
  display:none;
  font-size:26px;
  background:none;
  border:none;
  color:white;
  cursor:pointer;
}

/* ===== MOBILE OVERLAY ===== */
.mobile-overlay{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.65);
  backdrop-filter:blur(6px);
  display:flex;
  justify-content:flex-end;
}

/* SLIDE MENU PANEL */
.mobile-menu{
  width:260px;
  height:100%;
  background:#0039C8;
  padding:40px 28px;
  display:flex;
  flex-direction:column;
  gap:26px;
  box-shadow:-8px 0 30px rgba(0,0,0,0.4);
}

.mobile-menu span{
  color:white;
  font-size:18px;
  cursor:pointer;
}

/* MOBILE CTA */
.mobile-cta{
  margin-top:20px;
  background:#A6FF00;
  border:none;
  padding:12px;
  font-weight:700;
  border-radius:10px;
  cursor:pointer;
}

/* MENU ANIMATION */
.menu-enter-active,
.menu-leave-active{
  transition:.3s ease;
}
.menu-enter-from,
.menu-leave-to{
  opacity:0;
}

/* RESPONSIVE */
@media (max-width:900px){
  .nav-links,
  .cta-btn{
    display:none;
  }

  .menu-btn{
    display:block;
    padding-left: 80%;
  }
  
}

</style>

