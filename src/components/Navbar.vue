<script setup lang="ts">
import { ref } from 'vue'
import { Close, Menu, Moon, Sun } from '../icons'

const LOCAL_STORAGE_KEY = 's_portfolio_theme'

const getInitialTheme = () => {
  if (typeof localStorage !== 'undefined' && localStorage.getItem(LOCAL_STORAGE_KEY)) {
    return localStorage.getItem(LOCAL_STORAGE_KEY) === 'dark'
  }
  return window.matchMedia('(prefers-color-scheme: dark)').matches
}

const isMenuOpen = ref(false)
const isDarkMode = ref(getInitialTheme())

if (isDarkMode.value) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

const toggleTheme = (event: MouseEvent) => {
  const x = event.clientX
  const y = event.clientY
  const endRadius = Math.hypot(Math.max(x, innerWidth - x), Math.max(y, innerHeight - y))

  const toggle = () => {
    isDarkMode.value = !isDarkMode.value
    if (isDarkMode.value) {
      document.documentElement.classList.add('dark')
      localStorage.setItem(LOCAL_STORAGE_KEY, 'dark')
    } else {
      document.documentElement.classList.remove('dark')
      localStorage.setItem(LOCAL_STORAGE_KEY, 'light')
    }
  }

  if (!document.startViewTransition) {
    toggle()
    return
  }

  const transition = document.startViewTransition(toggle)

  transition.ready.then(() => {
    document.documentElement.animate(
      {
        clipPath: [`circle(0px at ${x}px ${y}px)`, `circle(${endRadius}px at ${x}px ${y}px)`],
      },
      {
        duration: 400,
        easing: 'ease-in',
        pseudoElement: '::view-transition-new(root)',
      },
    )
  })
}
</script>

<template>
  <header class="w-full h-22 px-6 py-5 md:py-6 relative border-b border-white/10">
    <nav
      class="absolute left-1/2 -translate-x-1/2 top-1/2 -translate-y-1/2 hidden md:flex items-center gap-8 text-xs font-mono uppercase tracking-widest text-foreground/75"
    >
      <!-- <a href="#" class="nav-link relative hover:text-foreground transition-colors">Home</a> -->
      <a href="#about" class="nav-link relative hover:text-foreground transition-colors">About</a>
      <a href="#projects" class="nav-link relative hover:text-foreground transition-colors"
        >Projects</a
      >
      <a href="#contact" class="nav-link relative hover:text-foreground transition-colors"
        >Contact</a
      >
    </nav>

    <div class="absolute right-4 top-1/2 -translate-y-1/2 flex items-center gap-4">
      <button
        type="button"
        @click="toggleTheme"
        class="p-2 text-foreground/75 hover:text-foreground transition-colors"
        aria-label="Toggle theme"
      >
        <Sun v-if="!isDarkMode" />
        <Moon v-else />
      </button>

      <a
        href="#contact"
        class="cta-btn hidden md:inline-block px-5 py-2 border border-accent text-accent font-mono text-xs uppercase tracking-widest hover:bg-accent hover:text-background transition-all duration-200"
      >
        Hire Me
      </a>

      <button
        @click="isMenuOpen = !isMenuOpen"
        class="md:hidden p-2 text-foreground"
        aria-label="Toggle menu"
      >
        <Menu v-if="!isMenuOpen" />
        <Close v-else />
      </button>
    </div>

    <Transition
      enter-active-class="transition ease-out duration-200"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition ease-in duration-150"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div
        v-if="isMenuOpen"
        class="absolute top-full left-0 right-0 bg-background border-b border-white/10 p-6 flex flex-col items-center gap-6 md:hidden z-50"
      >
        <!-- <a href="#" @click="isMenuOpen = false" class="font-mono text-sm uppercase tracking-widest"
          >Home</a
        > -->
        <a
          href="#about"
          @click="isMenuOpen = false"
          class="font-mono text-sm uppercase tracking-widest"
          >About</a
        >
        <a
          href="#projects"
          @click="isMenuOpen = false"
          class="font-mono text-sm uppercase tracking-widest"
          >Projects</a
        >
        <a
          href="#contact"
          @click="isMenuOpen = false"
          class="font-mono text-sm uppercase tracking-widest"
          >Contact</a
        >
        <a
          href="#contact"
          @click="isMenuOpen = false"
          class="px-6 py-2 border border-accent text-accent font-mono text-xs uppercase tracking-widest"
          >Hire Me</a
        >
      </div>
    </Transition>
  </header>
</template>

<style>
::view-transition-old(root),
::view-transition-new(root) {
  animation: none;
  mix-blend-mode: normal;
}
</style>
