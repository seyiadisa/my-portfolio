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

const isDarkMode = ref(getInitialTheme())

if (isDarkMode.value) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

const isMenuOpen = ref(false)

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
  <header class="w-full px-6 py-4 md:py-6 flex justify-end items-center relative">
    <div class="flex items-center gap-2 md:gap-12">
      <nav class="hidden md:flex items-center gap-8 text-lg font-medium">
        <a href="#about">About</a>
        <a href="#projects">My Work</a>
        <a href="#contact">Contact</a>
      </nav>

      <button type="button" @click="toggleTheme" class="p-4">
        <Sun v-if="!isDarkMode" />
        <Moon v-else />
      </button>

      <button @click="isMenuOpen = !isMenuOpen" class="md:hidden p-2" aria-label="Toggle menu">
        <Close v-if="!isMenuOpen" />
        <Menu v-else />
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
        class="absolute top-full right-0 w-full bg-background border-b border-accent/20 p-6 flex flex-col items-center gap-6 md:hidden z-50 shadow-lg"
      >
        <a href="#about" @click="isMenuOpen = false" class="text-lg font-medium">About</a>
        <a href="#projects" @click="isMenuOpen = false" class="text-lg font-medium">My Work</a>
        <a href="#contact" @click="isMenuOpen = false" class="text-lg font-medium">Contact</a>
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
