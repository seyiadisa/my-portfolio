<script setup lang="ts">
import gsap from 'gsap'
import { onMounted, useTemplateRef } from 'vue'

const cyclingText = useTemplateRef('cyclingText')

onMounted(() => {
  const tl = gsap.timeline({ defaults: { ease: 'power4.out' } })

  tl.to('#heroLabel', {
    opacity: 1,
    y: 0,
    duration: 1,
    delay: 0.3,
  })
    .to(
      '#heroTitle',
      {
        opacity: 1,
        y: 0,
        duration: 1.2,
        stagger: 0.1,
      },
      '-=0.6',
    )
    .to(
      '#cyclingText',
      {
        opacity: 1,
        y: 0,
        duration: 1,
      },
      '-=0.8',
    )
    .to(
      '#staticDescription',
      {
        opacity: 1,
        y: 0,
        duration: 1,
      },
      '-=0.6',
    )
    .to(
      '#ctaContainer',
      {
        opacity: 1,
        y: 0,
        duration: 1,
      },
      '-=0.6',
    )

  const roles = [
    'Fullstack Developer',
    '',
    'Creative Technologist',
    '',
    'AI Integration Specialist',
    '',
  ]

  const cycle = gsap.timeline({
    defaults: { ease: 'power1.inOut' },
    delay: 4.5,
    repeat: -1,
  })

  roles.forEach((role, i) => {
    cycle.add(gsap.to(cyclingText.value, { text: { value: role, rtl: i % 2 !== 0 }, duration: 2 }))
  })
})
</script>

<template>
  <section class="flex flex-1 items-center relative px-4 md:px-16">
    <div class="max-w-7xl mx-auto w-full">
      <div id="heroContent" class="w-full">
        <div id="heroLabel" class="text-sm tracking-[0.2em] uppercase mb-8 font-medium opacity-0">
          Software Engineer
        </div>

        <h1
          id="heroTitle"
          class="font-display text-3xl md:text-5xl lg:text-6xl mb-8 tracking-tight opacity-0"
        >
          OLUWASEYI<br />ADISA
        </h1>

        <p
          ref="cyclingText"
          id="cyclingText"
          class="text-lg md:text-xl h-4 lg:text-2xl font-display mb-8 opacity-0 text-accent"
        ></p>

        <div id="staticDescription" class="space-y-4 max-w-3xl mb-12 opacity-0">
          <p class="leading-relaxed">
            I create intelligent, user-focused applications that merge design, scalability, and
            performance into meaningful digital experiences.
          </p>
          <p class="leading-relaxed">
            I build AI-powered systems and modern APIs that help businesses and ideas scale
            confidently.
          </p>
          <p class="leading-relaxed">I don't just write code — I craft solutions that last.</p>
        </div>

        <div id="ctaContainer" class="flex gap-8 flex-wrap opacity-0">
          <a
            href="#projects"
            class="group relative inline-block px-10 py-4 border-3 font-medium uppercase tracking-widest text-sm transition-all duration-300 overflow-hidden hover:border-accent"
          >
            <span class="relative z-10 transition-colors duration-300">View Work</span>
            <span
              class="absolute inset-0 bg-accent w-0 group-hover:w-full transition-all duration-300"
            ></span>
          </a>
          <a
            href="#contact"
            class="group relative inline-block px-10 py-4 border-3 border-accent text-accent font-medium uppercase tracking-widest text-sm transition-all duration-300 overflow-hidden"
          >
            <span class="relative group-hover:text-foreground z-10 transition-colors duration-300"
              >Get in Touch</span
            >
            <span
              class="absolute inset-0 bg-accent w-0 group-hover:w-full transition-all duration-300"
            ></span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
