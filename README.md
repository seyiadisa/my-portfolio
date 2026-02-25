# Oluwaseyi Adisa - Portfolio Website

Personal portfolio website built with Vue 3, TypeScript, Vite, Tailwind CSS v4, and GSAP.

## Overview

This project showcases my work, background, and contact channels in a clean, animated single-page experience.

Sections include:

- Hero introduction
- About
- Selected projects
- Contact and social links

## Tech Stack

- Vue 3 (`<script setup>` + TypeScript)
- Vite
- Tailwind CSS v4
- GSAP + ScrollTrigger

## Features

- Smooth in-page anchor scrolling
- Scroll-triggered reveal animations
- Interactive project cards
- Responsive navigation with mobile menu
- Dark/light theme toggle with persisted preference
- Contact CTA with direct email link

## Getting Started

### Prerequisites

- Node.js 18+
- bun

### Install

```bash
bun install
```

### Run Development Server

```bash
bun run dev
```

### Build for Production

```bash
bun run build
```

### Preview Production Build

```bash
bun run preview
```

### Format Source Files

```bash
bun run format
```

## Project Structure

```text
src/
  components/
    Navbar.vue
    Hero.vue
    About.vue
    Projects.vue
    ProjectCard.vue
    Footer.vue
  assets/
  types/
  App.vue
```

## Deployment

Build output is generated in `dist/` and can be deployed to any static host (Vercel, Netlify, Cloudflare Pages, GitHub Pages, etc.).

## License

This repository contains personal portfolio source code.
