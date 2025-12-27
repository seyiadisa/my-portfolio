<script setup lang="ts"></script>

<template>
  <div class="bg-effects">
    <div class="shape shape-1"></div>
    <div class="shape shape-2"></div>
  </div>
  <p class="text-4xl font-bold mb-4">Welcome to My Portfolio</p>
</template>

<style scoped>
.bg-effects {
  position: fixed;
  inset: 0;
  z-index: -1;
  pointer-events: none;
  overflow: hidden;
}

.shape {
  position: absolute;
  width: 300px;
  height: 300px;
  border-radius: 40%;
  filter: blur(40px);
  opacity: 0.35;
  background: linear-gradient(135deg, rgba(0, 153, 255, 0.6), rgba(140, 0, 255, 0.6));
}

.shape-1 {
  top: 0%;
  left: 0%;
  transform: translate(-25%, -25%);
  transform-origin: center;
  width: 32rem;
  height: 32rem;
}
.shape-2 {
  bottom: -40%;
  right: 15%;
  width: 40rem;
  height: 40rem;
}
</style>
