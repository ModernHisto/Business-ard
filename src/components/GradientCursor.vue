<template>
  <div class="cursor-wrapper">
    <div class="background-layer"></div>
    <div class="gradient-cursor" :style="cursorStyle"></div>

    <div class="content-layer">
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const cursorPosition = ref({ x: 0, y: 0 })
const cursorStyle = ref({})

const updateCursorPosition = (e) => {
  cursorPosition.value = { x: e.clientX, y: e.clientY }
  cursorStyle.value = {
    left: `${cursorPosition.value.x}px`,
    top: `${cursorPosition.value.y}px`,
    opacity: '1'
  }
}

const handleMouseLeave = () => {
  cursorStyle.value = { ...cursorStyle.value, opacity: '0' }
}

onMounted(() => {
  window.addEventListener('mousemove', updateCursorPosition)
  document.addEventListener('mouseleave', handleMouseLeave)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', updateCursorPosition)
  document.removeEventListener('mouseleave', handleMouseLeave)
})
</script>

<style lang="scss" scoped>
.cursor-wrapper {
  position: relative;
  width: 100%;
  min-height: 100vh;
  z-index: 10;
}

.background-layer {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url(@/assets/svg/background.svg);
  background-size: cover;
  z-index: 1;
}

.gradient-cursor {
  position: fixed;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  background: radial-gradient(circle,
      rgba(102, 253, 15, 0.8) 0%,
      rgba(102, 253, 15, 0.4) 30%,
      rgba(102, 253, 15, 0.2) 50%,
      transparent 70%);
  pointer-events: none;
  transform: translate(-50%, -50%);

  opacity: 0;
  transition: opacity 0.3s ease;
  filter: blur(1px);
}

.content-layer {
  position: relative;
  z-index: 100;
  pointer-events: auto;
}

@include down($lg) {
  .gradient-cursor {
    display: none;
  }
}
</style>