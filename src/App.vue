<script setup lang="ts">
import { onMounted, useTemplateRef } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import TextPlugin from 'gsap/TextPlugin'
import { ScrollToPlugin } from 'gsap/ScrollToPlugin'

import Footer from './components/Footer.vue'
import Hero from './components/Hero.vue'
import Navbar from './components/Navbar.vue'
import Projects from './components/Projects.vue'

const loaderContainer = useTemplateRef('loader-container')

onMounted(() => {
  if (!loaderContainer.value) {
    return null
  }

  gsap.registerPlugin(ScrollTrigger, TextPlugin, ScrollToPlugin)

  const tl = gsap.timeline()

  tl.to('#progress-fill', {
    width: '100%',
    duration: 2.5,
    ease: 'expo.inOut',
    onUpdate: function () {
      const pct = Math.round(this.progress() * 100)
      const loaderPercentage = loaderContainer.value?.querySelector(
        '#load-percentage',
      ) as HTMLDivElement
      if (loaderPercentage) {
        loaderPercentage.innerText = pct.toString().padStart(2, '0')
      }
    },
  })
    .to('#loader-ui', { opacity: 0, y: -20, duration: 0.5 })
    .to('.loader-column', {
      scaleY: 0,
      duration: 1.2,
      stagger: 0.1,
      ease: 'expo.inOut',
    })
    .set('#loader-container', { display: 'none' })
    .to('#heroTitle', { opacity: 1, y: 0, duration: 1 }, '-=0.5')

  document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
    anchor.addEventListener('click', function (e) {
      e.preventDefault()

      const href = anchor.getAttribute('href')

      const target = document.querySelector(href ?? '')
      if (target) {
        target.scrollIntoView({
          behavior: 'smooth',
          block: 'start',
        })
      }
    })
  })
})
</script>

<template>
  <div class="max-w-7xl mx-auto space-y-20">
    <div class="min-h-screen flex flex-col relative">
      <Navbar />
      <Hero />
    </div>

    <section id="projects">
      <Projects />
    </section>

    <Footer />
  </div>

  <div
    ref="loader-container"
    id="loader-container"
    class="fixed inset-0 z-100 flex flex-col items-center justify-center bg-background"
  >
    <div
      class="loader-grid absolute inset-0 grid grid-cols-5 z-1 *:bg-accent *:scale-y-100 *:origin-bottom"
    >
      <div class="loader-column"></div>
      <div class="loader-column"></div>
      <div class="loader-column"></div>
      <div class="loader-column"></div>
      <div class="loader-column"></div>
    </div>
    <div id="loader-ui" class="relative z-10 w-4/5 max-w-lg mix-blend-difference">
      <div class="flex justify-between items-end font-display">
        <span class="text-accent text-2xl">LOADING</span>
        <span id="load-percentage" class="text-accent text-6xl">00</span>
      </div>
      <div class="progress-bar-container w-full h-5 border-2 border-accent mt-5">
        <div id="progress-fill" class="h-full w-0 bg-accent"></div>
      </div>
    </div>
  </div>
</template>
