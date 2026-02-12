<template>
  <div class="brand-strip">
    <div class="brand-track">

      <!-- FIRST SET -->
      <div class="brand" v-for="(logo, i) in logos" :key="'a'+i">
        <img :src="logo" alt="brand" />
      </div>

      <!-- DUPLICATE SET (IMPORTANT for infinite effect) -->
      <div class="brand" v-for="(logo, i) in logos" :key="'b'+i">
        <img :src="logo" alt="brand" />
      </div>

    </div>
  </div>
</template>

<script setup>
import l1 from '../assets/images/brands/carosel1.PNG'
import l2 from '../assets/images/brands/carosel2.PNG'
import l3 from '../assets/images/brands/carosel3.PNG'
import l4 from '../assets/images/brands/carosel4.PNG'
import l5 from '../assets/images/brands/carosel5.PNG'
import l6 from '../assets/images/brands/carosel6.JPG'
import l7 from '../assets/images/brands/carosel7.png'

const logos = [l1, l2, l3, l4, l5, l6, l7]
</script>

<style scoped>

/* ===== OUTER STRIP ===== */
.brand-strip{
  width:100%;
  overflow:hidden;
  background:#ffffff;
  padding:18px 0;
  border-bottom:1px solid #eaeaea;
}

/* ===== MOVING TRACK ===== */
.brand-track{
  display:flex;
  width:max-content;
  animation:scroll 25s linear infinite;
}

/* LOGO ITEM */
.brand{
  flex:0 0 auto;
  padding:0 50px;
  display:flex;
  align-items:center;
  justify-content:center;
}

/* LOGO IMAGE */
.brand img{
  height:38px;
  width:auto;
  transition:0.25s ease;
}

.brand img:hover{
  filter: grayscale(0%);
  opacity:1;
  transform:scale(1.08);
}

/* ===== INFINITE ANIMATION ===== */
@keyframes scroll{
  from{
    transform:translateX(0);
  }
  to{
    transform:translateX(-50%);
  }
}

/* MOBILE SPEED */
@media(max-width:768px){
  .brand-track{
    animation:scroll 15s linear infinite;
  }
  .brand img{
    height:26px;
  }
}
.brand-strip:hover .brand-track{
  animation-play-state: paused;
}


</style>
