<template>
  <nav class="navbar">
    <div class="container nav-inner">
      <!-- LEFT: LOGO -->
      <div class="nav-left">
        <span class="logo">PEBBLE</span>
      </div>

      <!-- CENTER: MENU -->
      <ul class="nav-links">
        <li>Services</li>
        <li>Use Cases</li>
        <li>Resources</li>
        <li>Pricing</li>
      </ul>

      <!-- RIGHT: CTA / MOBILE -->
      <div class="nav-right">
        <button class="cta-btn">Get Started</button>

        <button
          class="menu-btn"
          @click="toggleMenu"
          aria-label="Toggle menu"
        >
          ☰
        </button>
      </div>
    </div>

    <!-- MOBILE MENU -->
    <div v-if="isOpen" class="mobile-menu">
      <span @click="toggleMenu">Services</span>
      <span @click="toggleMenu">Use Cases</span>
      <span @click="toggleMenu">Resources</span>
      <span @click="toggleMenu">Pricing</span>
      <button class="mobile-cta">Get Started</button>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const isOpen = ref(false)
const toggleMenu = () => (isOpen.value = !isOpen.value)
</script>

<style scoped>
/* ===== BASE ===== */
.navbar {
  background: #0039C8;
  position: sticky;
  top: 0;
  z-index: 1000;
}

.container {
  max-width: 1320px;
  margin: auto;
  padding: 0 24px;
}

/* ===== INNER LAYOUT ===== */
.nav-inner {
  height: 80px;
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
}

/* LEFT */
.logo {
  color: #ffffff;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 1px;
}

/* CENTER MENU */
.nav-links {
  display: flex;
  justify-content: center;
  gap: 36px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links li {
  color: #ffffff;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  position: relative;
}

/* underline (figma-like) */
.nav-links li::after {
  content: '';
  position: absolute;
  left: 50%;
  bottom: -10px;
  width: 0;
  height: 2px;
  background: #a6ff00;
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.nav-links li:hover::after {
  width: 100%;
}

/* RIGHT */
.nav-right {
  display: flex;
  align-items: center;
  gap: 16px;
}

.cta-btn {
  background: #ffffff;
  color: #0a4cff;
  border: none;
  padding: 10px 18px;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
}

/* MOBILE BUTTON */
.menu-btn {
  display: none;
  font-size: 26px;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
}

/* ===== MOBILE MENU ===== */
.mobile-menu {
  background: #0039C8;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 24px;
}

.mobile-menu span {
  color: white;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
}

.mobile-cta {
  margin-top: 10px;
  background: #a6ff00;
  border: none;
  padding: 12px;
  font-weight: 600;
  border-radius: 8px;
  cursor: pointer;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 900px) {
  .nav-links,
  .cta-btn {
    display: none;
  }

  .menu-btn {
    display: block;
  }
}
</style>
