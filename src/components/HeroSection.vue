<script setup>
import hero1 from '@/assets/images/hero2.jpg'
</script>

<template>
  <section class="hero hero-section">
    <div class="hero-images">
      <img :src="hero1" alt="hero" />
    </div>
  </section>
</template>

<style scoped>
/* HERO SECTION */
.hero{
  position:relative;
  width:100%;
  height:clamp(520px, 92vh, 900px);
  overflow:hidden;
}

/* IMAGE WRAPPER */
.hero-images{
  position:absolute;
  inset:0;
  width:100%;
  height:100%;
  display:flex;
}

/* DESKTOP IMAGE */
.hero-images img{
  width:100%;
  height:100%;
  object-fit:cover;
  object-position:center;
  display:block;
  /* FIX washed colors */
  filter: contrast(1.12) saturate(1.08) brightness(.95);
}


/* slight overlay (gives professional look) */
.hero::after{
  content:'';
  position:absolute;
  inset:0;
  pointer-events:none;
}


/* ================= MOBILE FIX ================= */
@media (max-width:768px){

  .hero{
    height:auto;
    min-height:auto;
    padding-top:0;
  }

  .hero-images{
    position:relative;
    height:auto;
  }

  .hero-images img{
    width:100%;
    height:auto;
    object-fit:contain;        /* IMPORTANT */
    object-position:top center;
  }
}

</style>