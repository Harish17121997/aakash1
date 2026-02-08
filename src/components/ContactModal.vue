<template>
  <transition name="fade">
    <div v-if="show" class="modal-overlay" @click.self="close">

      <!-- FORM CARD -->
      <div class="modal-card" v-if="!submitted">

        <div class="modal-header">
          <h2>Get in Touch</h2>
          <button class="close-btn" @click="close">✕</button>
        </div>

        <form @submit.prevent="submitForm" class="form">

          <div class="field">
            <label>Full Name</label>
            <input v-model="form.name" required type="text" placeholder="Enter your full name" />
          </div>

          <div class="field">
            <label>Company Name</label>
            <input v-model="form.company" type="text" placeholder="Your company name" />
          </div>

          <div class="field">
            <label>Ad Brief</label>
            <textarea
              v-model="form.brief"
              rows="4"
              required
              placeholder="Describe your ad brief..."
            ></textarea>
          </div>

          <div class="field">
            <label>Budget</label>
            <input v-model="form.budget" type="text" placeholder="Approx budget (₹)" />
          </div>

          <button class="submit-btn">Submit Information</button>

        </form>
      </div>

      <!-- SUCCESS SCREEN -->
      <div class="success-card" v-else>
        <h2>Thank You 🎉</h2>
        <p>Someone from the team will reach out to you in the next 12-24 hours</p>
        <button class="ok-btn" @click="close">OK</button>
      </div>

    </div>
  </transition>
</template>

<script setup>
import { reactive, ref } from 'vue'

const props = defineProps({
  show: Boolean
})

const emit = defineEmits(['close'])

const form = reactive({
  name: '',
  company: '',
  brief: '',
  budget: ''
})

const submitted = ref(false)

const close = () => {
  submitted.value = false

  // reset form also
  form.name = ''
  form.company = ''
  form.brief = ''
  form.budget = ''

  emit('close')
}

const submitForm = () => {
  console.log('Form Data:', form)

  // simulate submit success
  submitted.value = true
}
</script>
<style scoped>
/* ===== GOOGLE FONT (very important) ===== */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

/* OVERLAY */
.modal-overlay{
  position:fixed;
  inset:0;
  background:rgba(8,12,22,0.75);
  backdrop-filter:blur(10px);
  display:flex;
  align-items:center;
  justify-content:center;
  padding:24px;
  z-index:2000;
  font-family:'Inter',system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
}

/* ===== MODAL CARD ===== */
.modal-card{
  width:560px;
  max-width:100%;
  background:linear-gradient(180deg,#ffffff 0%,#f7f9ff 100%);
  border-radius:22px;
  padding:32px;
  box-shadow:
    0 40px 80px rgba(0,0,0,0.35),
    0 2px 6px rgba(0,0,0,0.12);
  animation:pop .28s cubic-bezier(.22,1,.36,1);
}

/* HEADER */
.modal-header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:24px;
}

.modal-header h2{
  margin:0;
  font-size:26px;
  font-weight:800;
  color:#0f172a;
  letter-spacing:-0.3px;
}

/* CLOSE BUTTON */
.close-btn{
  border:none;
  background:#eef2ff;
  width:36px;
  height:36px;
  border-radius:10px;
  font-size:18px;
  cursor:pointer;
  transition:.2s;
}

.close-btn:hover{
  background:#dbe4ff;
  transform:rotate(90deg);
}

/* ===== FORM ===== */
.form{
  display:flex;
  flex-direction:column;
  gap:18px;
}

/* FIELD */
.field{
  display:flex;
  flex-direction:column;
  gap:7px;
}

.field label{
  font-size:13px;
  font-weight:600;
  color:#344054;
  letter-spacing:.2px;
}

/* INPUTS */
.field input,
.field textarea{
  border:1.5px solid #e4e7ec;
  background:#ffffff;
  border-radius:12px;
  padding:14px 14px;
  font-size:14px;
  font-family: 'Courier New', Courier, monospace;
  font-weight:500;
  color:#111827;
  transition:all .2s ease;
}

.field textarea{
  resize:none;
  min-height:110px;
}

/* FOCUS EFFECT */
.field input:focus,
.field textarea:focus{
  outline:none;
  border-color:#4577f5;
  box-shadow:0 0 0 4px rgba(69,119,245,0.15);
  background:#fff;
}

/* PLACEHOLDER */
.field input::placeholder,
.field textarea::placeholder{
  color:#98a2b3;
  font-weight:400;
}

/* ===== SUBMIT BUTTON ===== */
.submit-btn{
  margin-top:10px;
  background:linear-gradient(135deg,#4577f5,#2447d8);
  color:white;
  border:none;
  padding:15px;
  border-radius:14px;
  font-weight:700;
  font-size:15px;
  letter-spacing:.2px;
  cursor:pointer;
  transition:all .25s ease;
}

.submit-btn:hover{
  transform:translateY(-2px);
  box-shadow:0 14px 28px rgba(69,119,245,0.45);
}

.submit-btn:active{
  transform:translateY(0);
  box-shadow:0 6px 12px rgba(69,119,245,0.25);
}

/* ===== SUCCESS SCREEN ===== */
.success-card{
  width:460px;
  max-width:100%;
  background:linear-gradient(180deg,#ffffff,#f7f9ff);
  padding:42px 36px;
  text-align:center;
  border-radius:22px;
  animation:pop .3s cubic-bezier(.22,1,.36,1);
  box-shadow:
    0 40px 80px rgba(0,0,0,0.35),
    0 2px 6px rgba(0,0,0,0.12);
}

.success-card h3{
  font-size:24px;
  margin:14px 0 10px;
  font-weight:800;
  color:#0f172a;
}

.success-card p{
  color:#475467;
  font-size:14px;
  line-height:1.6;
}

/* OK BUTTON */
.ok-btn{
  margin-top:24px;
  background:#4577f5;
  color:white;
  border:none;
  padding:13px 28px;
  border-radius:14px;
  font-weight:600;
  cursor:pointer;
  transition:.25s;
}

.ok-btn:hover{
  transform:translateY(-2px);
  box-shadow:0 12px 24px rgba(69,119,245,0.35);
}

/* ===== ANIMATION ===== */
@keyframes pop{
  from{ transform:translateY(20px) scale(.95); opacity:0 }
  to{ transform:translateY(0) scale(1); opacity:1 }
}

/* FADE */
.fade-enter-active,
.fade-leave-active{
  transition:opacity .25s ease;
}

.fade-enter-from,
.fade-leave-to{
  opacity:0;
}

/* ===== MOBILE ===== */
@media (max-width:600px){

  .modal-card{
    padding:22px;
    border-radius:18px;
  }

  .modal-header h2{
    font-size:20px;
  }

  .success-card{
    padding:32px 24px;
  }
}

</style>
