<template>
  <section class="about">

    <!-- Floating images -->
    <img class="float img-1" src="../assets/images/about/about.png" />
    <img class="float img-2" src="../assets/images/about/about1.jpeg" />
    <img class="float img-3" src="../assets/images/about/about1.png" />

    <div class="about-container">

      <span class="label">Why Choose Pebble</span>

      <h3 class="headline">
        We Are A Creative Platform That Helps Brands Produce
        Authentic, High-Quality Video Content With Ease.
      </h3>

      <p class="description">
        By connecting businesses with talented creators, we enable the
        creation of impactful product ads, real estate ads, and TV commercials
        that truly resonate with audiences.
        <br /><br />
        Our approach is built around simplicity, trust, and collaboration—so
        brands can focus on growth while we take care of the creative process.
      </p>

    </div>
  </section>
</template>

<style scoped>
.about {
  position: relative;
  background: #000;
  color: #fff;
  padding: 180px 20px;
  overflow: hidden;
}

/* CONTAINER */
.about-container {
  max-width: 900px;
  margin: auto;
  text-align: center;
  position: relative;
  z-index: 5;
}

/* BIG LABEL */
.label {
  display: block;
  font-size: 64px;
  font-weight: 900;
  letter-spacing: 4px;
  opacity: 0.59;
  margin-bottom: 60px;
}

/* HEADLINE */
.headline {
  font-size: 22px;
  font-weight: 600;
  line-height: 1.6;
  margin-bottom: 28px;
  max-width: 820px;
  margin-left: auto;
  margin-right: auto;
}

/* DESCRIPTION */
.description {
  font-size: 14px;
  line-height: 1.9;
  color: #cfcfcf;
  max-width: 700px;
  margin: auto;
}

/* FLOATING IMAGES */
.float {
  position: absolute;
  object-fit: cover;
  border-radius: 16px;
  box-shadow: 0 30px 80px rgba(0,0,0,0.7);
  z-index: 2;
}

/* LEFT TOP */
.img-1 {
  width: 180px;
  top: 120px;
  left: 100px;
}

/* CENTER HERO IMAGE */
.img-2 {
  width: 320px;
  left: 80%;
  transform: translateX(-50%);
  z-index: 3;
}

/* LEFT BOTTOM */
.img-3 {
  width: 220px;
  bottom: 100px;
  left: 140px;
}

/* RESPONSIVE */
/* ================= TABLET ================= */
@media (max-width:1024px){

  .about{
    padding:120px 20px 90px;
  }

  .label{
    font-size:42px;
    letter-spacing:2px;
    margin-bottom:40px;
  }

  .headline{
    font-size:19px;
    line-height:1.7;
  }

  .description{
    font-size:14px;
  }

  /* reduce floating image size instead of hiding */
  .img-1{
    width:130px;
    left:30px;
    top:60px;
  }

  .img-2{
    width:240px;
    right:30px;
    left:auto;
    transform:none;
    top:160px;
  }

  .img-3{
    width:150px;
    left:40px;
    bottom:40px;
  }
}


/* ================= MOBILE ================= */
@media (max-width:768px){

  .about{
    padding:80px 18px 70px;
  }

  .about-container{
    text-align:center;
  }

  /* Title */
  .label{
    font-size:26px;
    letter-spacing:1px;
    margin-bottom:22px;
    opacity:.8;
  }

  .headline{
    font-size:17px;
    line-height:1.7;
    margin-bottom:20px;
  }

  .description{
    font-size:13.5px;
    line-height:1.85;
    color:#d4d4d4;
  }

  /* Turn floating images into a stacked gallery */
  .float{
    position:relative;
    display:block;
    margin:22px auto;
    left:auto;
    right:auto;
    top:auto;
    bottom:auto;
    transform:none;
    width:100%;
    max-width:320px;
    border-radius:14px;
    box-shadow:0 18px 40px rgba(0,0,0,.55);
  }

  /* order of images */
  .img-2{ order:1; }
  .img-1{ order:2; }
  .img-3{ order:3; }

  /* container becomes flex column */
  .about{
    display:flex;
    flex-direction:column;
    align-items:center;
  }

  .about-container{
    order:0;
    margin-bottom:10px;
  }
}


/* ================= SMALL PHONES ================= */
@media (max-width:420px){

  .about{
    padding:70px 14px 60px;
  }

  .label{
    font-size:22px;
  }

  .headline{
    font-size:16px;
  }

  .description{
    font-size:13px;
  }

  .float{
    max-width:280px;
  }
}

</style>