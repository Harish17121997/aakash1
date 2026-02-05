<script setup>
import hero1 from '@/assets/images/hero1.png'
</script>

<template>
  <section class="hero hero-section">
    <div class="hero-images">
      <img :src="hero1" alt="hero" />
    </div>
  </section>
</template>

<style scoped>
.hero {
  background: #0b3cff;
  color: white;
  overflow: hidden;
}

.hero-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 60px;
}

.hero h1 {
  font-size: 56px;
  line-height: 1.1;
}

.hero p {
  max-width: 420px;
  margin: 20px 0 30px;
}

.primary-btn {
  background: white;
  color: #0b3cff;
  border: none;
  padding: 14px 28px;
  border-radius: 30px;
  font-weight: 600;
  cursor: pointer;
}


@media (max-width: 768px) {
  .hero-inner {
    flex-direction: column;
    text-align: center;
  }

  .hero h1 {
    font-size: 40px;
  }

  .hero-images {
    justify-content: center;
  }
}
</style>