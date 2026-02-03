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
  <section id="projects" class="py-32 border-t-3 px-4 md:px-16">
    <div class="max-w-7xl mx-auto">
      <div class="flex justify-between items-baseline mb-16 gap-8 flex-wrap">
        <h2 class="section-title font-display text-5xl md:text-6xl lg:text-7xl tracking-tight">
          FEATURED PROJECTS
        </h2>
      </div>
    </div>

    <div class="w-full">
      <ProjectCard
        :key="i"
        v-for="(project, i) in projects"
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
