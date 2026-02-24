<script setup lang="ts">
import { onMounted } from 'vue'
import type { Project } from '../types/project'
import gsap from 'gsap'

const props = defineProps<Project>()

onMounted(() => {
  gsap.from('.project-card', {
    y: 50,
    opacity: 0,
    duration: 0.8,
    stagger: 0.2,
    ease: 'power3.out',
    scrollTrigger: { trigger: '#projects', start: 'top 75%', once: true },
  })

  document.querySelectorAll<HTMLElement>('.project-card').forEach((card) => {
    card.addEventListener('mouseenter', () => {
      gsap.to(card, { y: -6, duration: 0.3, ease: 'power2.out' })
    })
    card.addEventListener('mouseleave', () => {
      gsap.to(card, { y: 0, duration: 0.35, ease: 'power2.inOut' })
    })
  })
})
</script>

<template>
  <article
    class="project-card grid md:grid-cols-2 border border-white/10 overflow-hidden transition-colors duration-300 hover:border-white/25"
    :class="index % 2 === 1 ? 'md:[direction:rtl]' : ''"
  >
    <div
      class="relative bg-white/5 min-h-64 md:min-h-80 overflow-hidden"
      :class="index % 2 === 1 ? '[direction:ltr]' : ''"
    >
      <img :src="props.imageUrl" :alt="props.title" class="w-full h-full object-cover" />
    </div>

    <div
      class="p-8 md:p-10 bg-[#0d1117] flex flex-col justify-center"
      :class="index % 2 === 1 ? '[direction:ltr]' : ''"
    >
      <h3 class="font-display font-black text-2xl md:text-3xl uppercase text-foreground mb-3">
        {{ props.title }}
      </h3>

      <p class="text-foreground/75 text-sm leading-relaxed mb-6">
        {{ props.description }}
      </p>

      <div class="flex flex-wrap gap-2 mb-8">
        <span
          v-for="(tech, i) in technologies"
          :key="i"
          class="px-3 py-1 border border-white/20 text-foreground/75 text-xs uppercase tracking-widest font-mono"
        >
          {{ tech }}
        </span>
      </div>

      <div class="flex items-center gap-6">
        <a
          :href="props.url"
          target="_blank"
          rel="noopener noreferrer"
          class="font-mono text-xs uppercase tracking-widest text-accent border-b border-accent pb-0.5 hover:opacity-70 transition-opacity"
        >
          Visit Site ↗
        </a>
      </div>
    </div>
  </article>
</template>
