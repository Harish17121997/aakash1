<template>
  <section class="how-work">
    <h2 class="title">HOW WE WORK</h2>

    <!-- Dotted Path -->
    <svg class="path" viewBox="0 0 1200 400" preserveAspectRatio="none">
      <path
        d="M50 120 C300 40, 450 200, 650 140 S950 220, 1150 160"
        fill="none"
        stroke="#d6d6d6"
        stroke-width="2"
        stroke-dasharray="6 8"
      />
    </svg>

    <div class="cards">
      <div
        v-for="(step, i) in steps"
        :key="i"
        class="card"
        :class="'card-' + (i + 1)"
      >
        <span class="badge">{{ step.no }}</span>
        <div class="content">
          <h4>{{ step.title }}</h4>
          <p>{{ step.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
const steps = [
  {
    no: '01',
    title: 'Share Your Brief',
    desc: 'Tell us about your brand, product and the style of videos you need.'
  },
  {
    no: '02',
    title: 'Get Matched With Creators',
    desc: 'We connect you with relevant UGC creators for your niche.'
  },
  {
    no: '03',
    title: 'Review & Select',
    desc: 'Browse profiles, samples and select creators you love.'
  },
  {
    no: '04',
    title: 'Creator Produces Content',
    desc: 'Creators film authentic high-quality UGC based on your brief.'
  },
  {
    no: '05',
    title: 'Review & Revisions',
    desc: 'Review videos and request changes if required.'
  },
  {
    no: '06',
    title: 'Download & Use Anywhere',
    desc: 'Use your UGC across ads, socials and campaigns.'
  }
]
</script>

<style scoped>
.how-work {
  position: relative;
  padding: 25px 20px;
  background: radial-gradient(circle at top, #eef2ff, #f8faff);
  overflow: hidden;
}

/* TITLE */
.title {
  text-align: center;
  font-size: 48px;
  font-weight: 900;
  margin-bottom: 80px;
}

/* PATH */
.path {
  position: absolute;
  top: 122px;
  left: 0;
  width: 100%;
  height: 300px;
  pointer-events: none;
}

/* CARDS WRAPPER */
.cards {
  max-width: 1200px;
  margin: auto;
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 80px 60px;
}

/* CARD */
.card {
  background: white;
  border-radius: 16px;
  padding: 24px;
  width: 280px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.08);
  position: relative;
  transform: rotate(-2deg);
  transition: all 0.3s ease;
}

.card:hover {
  transform: rotate(0deg) translateY(-6px);
}

/* BADGE */
.badge {
  position: absolute;
  top: -18px;
  left: 20px;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  color: #fff;
  font-size: 14px;
  font-weight: 700;
  display: grid;
  place-items: center;
}

/* CONTENT */
.content h4 {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 8px;
}

.content p {
  font-size: 13px;
  color: #555;
  line-height: 1.5;
}

/* COLORS */
.card-1 .badge { background: #ff7a59; }
.card-2 .badge { background: #6c63ff; }
.card-3 .badge { background: #a855f7; }
.card-4 .badge { background: #22c55e; }
.card-5 .badge { background: #ec4899; }
.card-6 .badge { background: #3b82f6; }

/* POSITIONING (ZIG-ZAG) */
.card-2 { transform: rotate(2deg); margin-top: -40px; }
.card-3 { margin-top: 10px; }
.card-4 { margin-top: -20px; }
.card-5 { transform: rotate(2deg); }
.card-6 { margin-top: -30px; }

/* RESPONSIVE */
@media (max-width: 900px) {
  .cards {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .card {
    width: 100%;
    transform: rotate(0);
  }

  .path {
    display: none;
  }

  .title {
    font-size: 36px;
  }
}
</style>
