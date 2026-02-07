<template>
  <footer class="footer">

    <!-- Newsletter -->
    <div class="newsletter">
      <h3>SUBSCRIBE TO OUR NEWSLETTER</h3>
      <p>Stay in the loop with everything you need to know.</p>

      <div class="newsletter-form">
        <input type="email" placeholder="Enter your email" />
        <button>Subscribe</button>
      </div>

      <span class="privacy">We care about your data in our privacy policy</span>
    </div>

    <!-- Footer Content -->
    <div class="footer-content">

      <!-- Brand -->
      <div class="brand">
        <h4>PEBBLE</h4>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit,
          sed do eiusmod.
        </p>
      </div>

      <!-- Company -->
      <div class="col">
        <h5>Company</h5>
        <a>About Us</a>
        <a>How It Works</a>
        <a>Careers</a>
        <a>Blog</a>
        <a>Contact Us</a>
      </div>

      <!-- Solutions -->
      <div class="col">
        <h5>Solutions</h5>
        <a>Product Ads</a>
        <a>Real Estate Ads</a>
        <a>TV Commercials</a>
        <a>UGC Videos</a>
        <a>Influencer Marketing</a>
      </div>

      <!-- Others -->
      <div class="col">
        <h5>Others</h5>
        <a>Blog</a>
        <a>Terms & Conditions</a>
        <a>Refund Policy</a>
        <a>Affiliate</a>
        <a>FAQ</a>
      </div>

      <!-- Subscribe -->
      <div class="col subscribe-col">
        <h5>Subscribe</h5>

        <div class="mini-subscribe">
          <input type="email" placeholder="Your Email Address" />
          <button>➜</button>
        </div>

        <div class="payments">
          <img src="../assets/images/footer/footer1.png" />
          <!-- <img src="../assets/images/mastercard.png" />
          <img src="../assets/images/paypal.png" /> -->
        </div>
      </div>

    </div>

    <!-- Bottom -->
    <div class="footer-bottom">
      © 2026 PEBBLE Media. All Rights Reserved.
    </div>

  </footer>
</template>


<script setup></script>
<style scoped>
.footer {
  background: #000;
  color: #fff;
  font-family: Inter, sans-serif;
}

/* NEWSLETTER */
.newsletter {
  background: #5b7cff;
  padding: 80px 20px;
  text-align: center;
}

.newsletter h3 {
  font-size: 28px;
  font-weight: 800;
  letter-spacing: 1px;
  margin-bottom: 10px;
}

.newsletter p {
  font-size: 14px;
  opacity: 0.9;
  margin-bottom: 30px;
}

.newsletter-form {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 12px;
}

.newsletter input {
  width: 260px;
  padding: 14px 18px;
  border-radius: 6px;
  border: none;
  outline: none;
}

.newsletter button {
  padding: 14px 28px;
  background: #fff;
  color: #000;
  border: none;
  border-radius: 6px;
  font-weight: 700;
  cursor: pointer;
}

.privacy {
  font-size: 12px;
  opacity: 0.8;
}

/* FOOTER CONTENT */
.footer-content {
  max-width: 1200px;
  margin: auto;
  padding: 80px 20px;
  display: grid;
  grid-template-columns: 1.4fr repeat(4, 1fr);
  gap: 40px;
}

.brand h4 {
  font-size: 24px;
  font-weight: 800;
  margin-bottom: 16px;
}

.brand p {
  font-size: 13px;
  line-height: 1.8;
  opacity: 0.7;
  max-width: 260px;
}

/* COLUMNS */
.col h5 {
  font-size: 14px;
  font-weight: 700;
  margin-bottom: 18px;
}

.col a {
  display: block;
  font-size: 13px;
  margin-bottom: 12px;
  opacity: 0.7;
  cursor: pointer;
}

.col a:hover {
  opacity: 1;
}

/* SUBSCRIBE MINI */
.mini-subscribe {
  display: flex;
  background: #111;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 20px;
}

.mini-subscribe input {
  flex: 1;
  background: transparent;
  border: none;
  padding: 12px;
  color: #fff;
  outline: none;
}

.mini-subscribe button {
  background: #5b7cff;
  border: none;
  padding: 0 16px;
  color: #fff;
  font-size: 18px;
  cursor: pointer;
}

/* PAYMENTS */
.payments img {
  height: 24px;
  margin-right: 10px;
}

/* BOTTOM */
.footer-bottom {
  border-top: 1px solid #222;
  padding: 20px;
  text-align: center;
  font-size: 12px;
  opacity: 0.6;
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .footer-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .brand p {
    margin: auto;
  }

  .mini-subscribe {
    max-width: 300px;
    margin: auto;
  }

  .payments {
    justify-content: center;
  }
}
</style>
