<script setup lang="ts">
import type { Project } from '../types/project'
import ProjectCard from './ProjectCard.vue'

import AudiophileImg from '../assets/images/audiophile.jpg'

const projects: Omit<Project, 'index'>[] = [
  {
    title: 'Audiophile',
    description: 'An e-commerce website for audio products.',
    url: 'https://audiophile-hub.vercel.app',
    imageUrl: AudiophileImg,
    technologies: ['React', 'Next.js', 'TypeScript', 'Tailwind', 'FastAPI'],
  },
]
</script>

<template>
  <section id="projects" class="py-20 border-t border-white/10 px-6 md:px-16">
    <div class="max-w-6xl mx-auto">
      <div class="section-heading mb-12">
        <span class="font-mono text-accent text-sm tracking-widest">02.</span>
        <h2
          class="font-display font-black text-4xl md:text-5xl lg:text-6xl uppercase tracking-tight text-foreground"
        >
          Projects
        </h2>
        <p class="font-mono text-xs uppercase tracking-widest text-foreground/75 mt-1">
          Selected Architectural Works
        </p>
      </div>
    </div>

    <div class="max-w-6xl mx-auto space-y-px">
      <ProjectCard
        v-for="(project, i) in projects"
        :key="i"
        :index="i"
        :title="project.title"
        :description="project.description"
        :url="project.url"
        :imageUrl="project.imageUrl"
        :technologies="project.technologies"
      />
    </div>
  </section>
</template>
