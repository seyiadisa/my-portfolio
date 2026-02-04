<script setup lang="ts">
import { computed /* onMounted */ } from 'vue'
import type { Project } from '../types/project'
// import gsap from 'gsap'
// import { ScrollTrigger } from 'gsap/ScrollTrigger'

const props = defineProps<Project>()

const formattedIndex = computed(() => {
  const i = props.index + 1
  return i < 10 ? `0${i}` : i
})

// onMounted(() => {
//   gsap.registerPlugin(ScrollTrigger)

//   gsap.utils.toArray<HTMLElement>('.project-card').forEach((card, index) => {
//     gsap.to(card, {
//       opacity: 1,
//       y: 0,
//       duration: 1,
//       delay: index * 0.2,
//       scrollTrigger: {
//         trigger: card,
//         start: 'top 80%',
//         toggleActions: 'play none none none',
//       },
//     })
//   })
// })
</script>

<template>
  <article
    class="project-card group border-3 transition-all duration-400 overflow-hidden"
  >
    <div class="w-full max-h-80 h-auto border-b-3 flex items-center justify-center overflow-hidden">
      <img :src="props.imageUrl" :alt="props.title" />
    </div>

    <div class="p-12">
      <div class="flex justify-between items-start mb-6 gap-4">
        <div class="text-5xl leading-none opacity-20">{{ formattedIndex }}</div>
      </div>
      <h3 class="text-3xl mb-4 tracking-tight">
        {{ props.title }}
      </h3>
      <p class="mb-8 leading-relaxed">
        {{ props.description }}
      </p>
      <div class="flex flex-wrap gap-3 mb-8">
        <span
          v-for="(tech, i) in technologies"
          :key="i"
          class="px-4 py-2 border-2 text-xs uppercase tracking-widest font-medium"
          >{{ tech }}</span
        >
      </div>
      <a
        :href="props.url"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center gap-3 font-medium uppercase tracking-widest text-sm py-3 border-b-2 hover:pl-4 hover:text-accent duration-300"
      >
        Visit Site
        <span class="transition-transform duration-300 hover:translate-x-2">→</span>
      </a>
    </div>
  </article>
</template>
