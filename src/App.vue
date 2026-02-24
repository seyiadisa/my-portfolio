<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

import Footer from './components/Footer.vue'
import Hero from './components/Hero.vue'
import Navbar from './components/Navbar.vue'
import Projects from './components/Projects.vue'
import About from './components/About.vue'

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)

  document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
    anchor.addEventListener('click', function (e) {
      e.preventDefault()
      const href = anchor.getAttribute('href')
      const target = document.querySelector(href ?? '')
      if (target) {
        target.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }
    })
  })

  gsap.utils.toArray<HTMLElement>('.section-heading').forEach((el) => {
    gsap.from(el, {
      y: 40,
      opacity: 0,
      duration: 0.8,
      ease: 'power3.out',
      scrollTrigger: { trigger: el, start: 'top 88%', once: true },
    })
  })
})
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <div class="min-h-screen flex flex-col">
      <Navbar />
      <Hero />
    </div>

    <About />
    <Projects />
    <Footer />
  </div>
</template>
