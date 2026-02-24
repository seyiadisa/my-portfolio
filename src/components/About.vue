<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
  gsap.from('.about-text', {
    y: 35,
    opacity: 0,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: '#about', start: 'top 80%', once: true },
  })
})
</script>

<template>
  <section id="about" class="py-20 border-t border-white/10 px-6 md:px-16">
    <div class="max-w-6xl mx-auto">
      <div class="section-heading mb-12">
        <span class="font-mono text-accent text-sm tracking-widest">01.</span>
        <h2
          class="font-display font-black text-4xl md:text-5xl lg:text-6xl uppercase tracking-tight text-foreground"
        >
          About Me
        </h2>
      </div>

      <div class="about-text space-y-8 max-w-3xl mb-12 *:leading-relaxed">
        <p>
          I help businesses design and build intelligent software that scales and drives growth.
          From modern APIs to AI-powered interfaces, I turn complex ideas into reliable products
          that perform in the real world, and continue to do so as your users and revenue grow.
        </p>

        <p>
          My focus is on outcomes, not just implementation. I think in terms of systems, trade-offs,
          and long-term value: clean architecture, fast user experiences, and technology decisions
          that reduce risk while unlocking new opportunities. The goal is always to ship products
          that are easy to extend, hard to break, and aligned with business objectives.
        </p>

        <p>
          When I&apos;m not building, I&apos;m reading or playing the keyboard, or just listening to
          a lot of music.
        </p>

        <p>
          If you&apos;re building a product meant to scale revenue, not technical debt, I&apos;m
          someone you want on your side.
        </p>
      </div>
    </div>
  </section>
</template>
