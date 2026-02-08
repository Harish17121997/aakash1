<template>
  <Navbar
    @go-services="scrollTo('services')"
    @go-usecases="scrollTo('usecases')"
    @go-resources="scrollTo('resources')"
    @go-pricing="scrollTo('pricing')"
    @open-contact="showContact = true"
  />

  <HeroSection />
  <BrandCarousel />

  <div ref="servicesRef">
    <ServicesSection />
  </div>

  <div ref="usecasesRef">
    <WorksSection />
  </div>

  <div ref="resourcesRef">
    <HowWeWork />
  </div>

  <div ref="pricingRef">
    <AboutSection />
  </div>
  <FooterSection />
  <ContactModal :show="showContact" @close="showContact = false" />
</template>

<script setup>
import { ref } from 'vue'

import Navbar from '@/components/Navbar.vue'
import HeroSection from '@/components/HeroSection.vue'
import ServicesSection from '@/components/ServicesSection.vue'
import WorksSection from '@/components/WorksSection.vue'
import HowWeWork from '@/components/HowWeWork.vue'
import AboutSection from '@/components/AboutSection.vue'
import FooterSection from '@/components/FooterSection.vue'
import BrandCarousel from '@/components/BrandCarousel.vue'
import ContactModal from '@/components/ContactModal.vue'
/* section refs */
const servicesRef = ref(null)
const usecasesRef = ref(null)
const resourcesRef = ref(null)
const pricingRef = ref(null)
const showContact = ref(false)

/* universal scroll function */
const scrollTo = (section) => {
  const map = {
    services: servicesRef,
    usecases: usecasesRef,
    resources: resourcesRef,
    pricing: pricingRef
  }

  map[section].value?.scrollIntoView({
    behavior: 'smooth',
    block: 'start'
  })
}
</script>
