<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
  const tl = gsap.timeline({ defaults: { ease: 'power3.out' } })

  tl.from('#hero-title-solid', { y: 50, opacity: 0, duration: 0.7 }, '-=0.2')
    .from('#hero-title-outline', { y: 50, opacity: 0, duration: 0.7 }, '-=0.5')
    .from('#hero-desc', { y: 20, opacity: 0, duration: 0.6 }, '-=0.3')
    .from('#hero-ctas', { y: 20, opacity: 0, duration: 0.5 }, '-=0.3')
})
</script>

<template>
  <section class="flex flex-1 items-center justify-center relative px-6 md:px-16 py-20">
    <div class="max-w-3xl mx-auto w-full text-center">
      <h1 class="font-display font-black uppercase leading-none mb-2">
        <span
          id="hero-title-solid"
          class="block text-6xl md:text-8xl lg:text-[9rem] tracking-tight text-foreground leading-none"
        >
          OLUWASEYI ADISA
        </span>
      </h1>
      <p
        id="hero-title-outline"
        class="block text-3xl md:text-4xl lg:text-5xl tracking-tight leading-none font-medium text-accent"
      >
        FULLSTACK DEVELOPER
      </p>

      <p
        id="hero-desc"
        class="mt-10 mb-10 text-foreground/75 max-w-xl mx-auto leading-relaxed text-sm md:text-base"
      >
        Engineering high-performance digital experiences. I specialize in building
        <span class="text-foreground font-medium">resilient architectures</span> and
        <span class="text-foreground font-medium">futuristic interfaces</span>.
      </p>

      <div id="hero-ctas" class="flex items-center justify-center gap-4 flex-wrap">
        <a
          href="#projects"
          class="cta-btn inline-flex items-center gap-2 px-8 py-3 bg-accent text-background font-mono text-xs uppercase tracking-widest font-bold hover:bg-accent/90 transition-all duration-200"
        >
          View Projects
          <span class="transition-transform duration-200 group-hover:translate-x-1">→</span>
        </a>
        <a
          href="#contact"
          class="cta-btn inline-flex items-center gap-2 px-8 py-3 border border-foreground/30 text-foreground font-mono text-xs uppercase tracking-widest hover:border-foreground transition-all duration-200"
        >
          Get In Touch
        </a>
      </div>
    </div>
  </section>
</template>
