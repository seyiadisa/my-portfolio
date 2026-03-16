<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

onMounted(() => {
  gsap.from('.footer-heading', {
    y: 40,
    opacity: 0,
    duration: 0.9,
    ease: 'power3.out',
    scrollTrigger: { trigger: '#contact', start: 'top 80%', once: true },
  })

  gsap.from('.footer-cta', {
    y: 30,
    opacity: 0,
    duration: 0.8,
    delay: 0.15,
    ease: 'power3.out',
    scrollTrigger: { trigger: '#contact', start: 'top 80%', once: true },
  })

  // gsap.from('.social-icon', {
  //   scale: 0.8,
  //   opacity: 0,
  //   duration: 0.4,
  //   stagger: 0.08,
  //   ease: 'back.out(1.5)',
  //   scrollTrigger: { trigger: '#contact', start: 'top 75%', once: true },
  // })

  document.querySelectorAll<HTMLElement>('.social-icon').forEach((icon) => {
    icon.addEventListener('mouseenter', () => {
      gsap.to(icon, { scale: 1.1, duration: 0.2, ease: 'power2.out' })
    })
    icon.addEventListener('mouseleave', () => {
      gsap.to(icon, { scale: 1, duration: 0.2, ease: 'power2.inOut' })
    })
  })

  document.querySelectorAll<HTMLElement>('.cta-btn').forEach((btn) => {
    btn.addEventListener('mousedown', () => {
      gsap.to(btn, { scale: 0.97, duration: 0.1, ease: 'power2.out' })
    })
    btn.addEventListener('mouseup', () => {
      gsap.to(btn, { scale: 1, duration: 0.2, ease: 'back.out(2)' })
    })
    btn.addEventListener('mouseleave', () => {
      gsap.to(btn, { scale: 1, duration: 0.2, ease: 'power2.inOut' })
    })
  })
})
</script>

<template>
  <footer id="contact" class="border-t border-white/10 py-20 px-6 md:px-16">
    <div class="max-w-6xl mx-auto">
      <div class="grid md:grid-cols-2 gap-16 mb-16 items-center">
        <div>
          <h2
            class="footer-heading font-display font-black text-4xl md:text-5xl lg:text-6xl uppercase tracking-tight text-foreground leading-tight mb-4"
          >
            LET'S BUILD<br />
            <span class="text-accent">THE FUTURE</span>
          </h2>
          <p class="text-foreground/75 text-sm leading-relaxed max-w-sm mb-10">
            I help businesses turn ideas into scalable products.
          </p>

          <div class="flex items-center gap-4">
            <a
              href="https://github.com/seyiadisa"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
              aria-label="GitHub"
            >
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
                />
              </svg>
            </a>
            <a
              href="https://x.com/SeyiAdisa1"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
              aria-label="X"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="18"
                height="18"
                viewBox="0 0 16 16"
                fill="currentColor"
              >
                <path
                  d="m9.237 7.004l4.84-5.505H12.93L8.727 6.28L5.371 1.5H1.5l5.075 7.228L1.5 14.499h1.147l4.437-5.047l3.545 5.047H14.5zM7.666 8.791l-.514-.72L3.06 2.344h1.762l3.302 4.622l.514.72l4.292 6.007h-1.761z"
                />
              </svg>
            </a>
            <a
              href="https://linkedin.com/in/oluwaseyi-adisa"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
              aria-label="LinkedIn"
            >
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                />
              </svg>
            </a>
            <a
              href="https://medium.com/@seyiadisaa"
              target="_blank"
              rel="noopener noreferrer"
              class="social-icon"
              aria-label="Medium"
            >
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M4.21 0A4.2 4.2 0 0 0 0 4.21v15.58A4.2 4.2 0 0 0 4.21 24h15.58A4.2 4.2 0 0 0 24 19.79v-1.093a5 5 0 0 1-.422.02c-2.577 0-4.027-2.146-4.09-4.832a8 8 0 0 1 .022-.708c.093-1.186.475-2.241 1.105-3.022a3.9 3.9 0 0 1 1.395-1.1c.468-.237 1.127-.367 1.664-.367h.023q.151 0 .303.01V4.211A4.2 4.2 0 0 0 19.79 0Zm.198 5.583h4.165l3.588 8.435l3.59-8.435h3.864v.146l-.019.004c-.705.16-1.063.397-1.063 1.254h-.003l.003 10.274c.06.676.424.885 1.063 1.03l.02.004v.145h-4.923v-.145l.019-.005c.639-.144.994-.353 1.054-1.03V7.267l-4.745 11.15h-.261L6.15 7.569v9.445c0 .857.358 1.094 1.063 1.253l.02.004v.147H4.405v-.147l.019-.004c.705-.16 1.065-.397 1.065-1.253V6.987c0-.857-.358-1.094-1.064-1.254l-.018-.004zm19.25 3.668c-1.086.023-1.733 1.323-1.813 3.124H24V9.298a1.4 1.4 0 0 0-.342-.047m-1.862 3.632c-.1 1.756.86 3.239 2.204 3.634v-3.634z"
                />
              </svg>
            </a>
          </div>
        </div>

        <div class="footer-cta">
          <p class="font-mono text-xs uppercase tracking-widest text-foreground/75 mb-4">
            Ready to start a project?
          </p>
          <a
            href="mailto:hello@seyiadisa.dev"
            class="group block text-xl md:text-2xl font-mono text-foreground hover:text-accent transition-colors duration-300 mb-8 break-all"
          >
            hello@seyiadisa.dev
            <span
              class="inline-block ml-2 transition-transform duration-300 group-hover:translate-x-2"
              >→</span
            >
          </a>
          <a
            href="mailto:hello@seyiadisa.dev?subject=Project%20Inquiry"
            class="cta-btn inline-flex items-center gap-3 px-8 py-3 bg-accent text-background font-mono text-xs uppercase tracking-widest font-bold hover:bg-accent/90 active:scale-95 transition-all duration-200"
          >
            Start a Project
            <span class="transition-transform duration-200 group-hover:translate-x-1">→</span>
          </a>
        </div>
      </div>

      <div
        class="border-t border-white/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4"
      >
        <p class="font-mono text-xs text-foreground/75">&copy; 2026 Oluwaseyi Adisa.</p>
      </div>
    </div>
  </footer>
</template>

<style lang="css" scoped>
.social-icon {
  width: 2.5rem;
  height: 2.5rem;
  border: 1px solid rgb(255 255 255 / 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-foreground);
  opacity: 60%;
  transition: all 200ms;
  cursor: pointer;
}

.social-icon:hover {
  color: var(--color-accent);
  border-color: var(--color-accent);
}
</style>
