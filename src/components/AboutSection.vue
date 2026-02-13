<template>
  <section class="about">

    <!-- Floating images -->
    <img class="float img-1" src="../assets/images/about/aboutads1.png" />
    <img class="float img-2" src="../assets/images/about/aboutads2.png" />
    <img class="float img-3" src="../assets/images/about/aboutads3.png" />

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
/* ================= SECTION ================= */
.about{
  position:relative;
  background: radial-gradient(circle at center,#0b0b0b 0%,#000 70%);
  color:#fff;
  padding:150px 20px 130px;
  overflow:hidden;
}

/* subtle glow background */
.about::before{
  content:"";
  position:absolute;
  width:700px;
  height:700px;
  background:radial-gradient(circle,rgba(70,120,255,.25),transparent 60%);
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  filter:blur(90px);
  z-index:0;
}

/* ================= CONTAINER ================= */
.about-container{
  max-width:820px;
  margin:auto;
  text-align:center;
  position:relative;
  z-index:5;
}

/* TITLE */
.label{
  display:block;
  font-size:58px;
  font-weight:800;
  letter-spacing:1px;
  margin-bottom:24px;
  color:#e6e6e6;
}

/* HEADLINE */
.headline{
  font-size:24px;
  font-weight:600;
  line-height:1.65;
  margin-bottom:20px;
}

/* DESCRIPTION */
.description{
  font-size:15px;
  line-height:1.9;
  color:#c9c9c9;
  max-width:680px;
  margin:auto;
}


/* ================= FLOATING IMAGES ================= */
.float{
  position:absolute;
  border-radius:22px;
  object-fit:cover;
  box-shadow:0 40px 100px rgba(0,0,0,.8);
  z-index:2;
  transition:transform .6s ease, box-shadow .4s ease;
}

/* LEFT TOP */
.img-1{
  width:200px;
  top:120px;
  left:8%;
  transform:rotate(-8deg);
}

/* RIGHT SIDE MAIN IMAGE */
.img-2{
  width:340px;
  right:6%;
  top:220px;
  /* transform:rotate(6deg); */
  z-index:3;
}

/* LEFT BOTTOM */
.img-3{
  width:240px;
  bottom:90px;
  left:8%;
  transform:rotate(-4deg);
}


/* ================= LAPTOP ================= */
@media (max-width:1366px){

  .img-1{
    width:200px;
    left:4%;
    top:130px;
  }

  .img-2{
    width:400px;
    right:4%;
    top:80%;
  }

  .img-3{
    width:200px;
    left:8%;
    bottom:80px;
  }

  .label{ font-size:46px; }
  .headline{ font-size:21px; }
}


/* ================= TABLET ================= */
@media (max-width:1024px){

  .about{
    padding:120px 20px 90px;
  }

  /* make images decorative */
  .float{
    opacity:.35;
  }

  .img-2{
    right:-40px;
  }

  .img-1{
    left:-30px;
  }

  .img-3{
    left:-10px;
  }

  .label{ font-size:38px; }
  .headline{ font-size:19px; }
}


/* ================= MOBILE ================= */
@media (max-width:768px){

  .about{
    padding:70px 16px 60px;
    display:flex;
    flex-direction:column;
    align-items:center;
  }

  /* important — removes desktop offsets */
  .float{
    position:static !important;
    inset:auto !important;
    top:auto !important;
    left:auto !important;
    right:auto !important;
    bottom:auto !important;

    display:block;
    width:92%;
    max-width:300px;
    margin:18px auto;

    transform:none !important;
    opacity:1;
  }

  .about-container{
    order:1;
    margin-bottom:10px;
    padding:0 6px;
  }

  /* order images like a story */
  .img-1{ order:2; }
  .img-2{ order:3; }
  .img-3{ order:4; }

  .label{
    font-size:26px;
    line-height:1.2;
    margin-bottom:14px;
  }

  .headline{
    font-size:16.5px;
    line-height:1.65;
  }

  .description{
    font-size:13.5px;
    line-height:1.85;
  }
}

</style>