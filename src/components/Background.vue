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

<template>
  <div class="background">

    <div class="background__edge-gradient background__edge-gradient--top"></div>
    <div class="background__edge-gradient background__edge-gradient--right"></div>
    <div class="background__edge-gradient background__edge-gradient--bottom"></div>
    <div class="background__edge-gradient background__edge-gradient--left"></div>
    
    <div class="background__corner-gradient background__corner-gradient--top-left"></div>
    <div class="background__corner-gradient background__corner-gradient--top-right"></div>
    <div class="background__corner-gradient background__corner-gradient--bottom-left"></div>
    <div class="background__corner-gradient background__corner-gradient--bottom-right"></div>

    <div class="background__layer background__layer--honeycomb"></div>
    <div class="background__layer background__layer--cursor-gradient" :style="cursorStyle"></div>

    <div class="background__content">
      <slot></slot>
    </div>
    
  </div>
</template>

<style lang="scss" scoped>
.background {
  position: relative;
  width: 100%;
  min-height: 100vh;
  z-index: 10;
  background: #0a0c0f;
  overflow: hidden;

  &::after {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at 50% 50%, transparent 30%, rgba(0, 0, 0, 0.2) 100%);
    pointer-events: none;
  }
}

.background__edge-gradient,
.background__corner-gradient {
  position: fixed;
  z-index: 0;
  pointer-events: none;
}

.background__edge-gradient {
  &--top {
    top: 0;
    left: 0;
    right: 0;
    height: 40vh;
    background: radial-gradient(
      ellipse at 50% 0%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(3.12rem);
    animation: topGlow 12s ease-in-out infinite alternate;
  }

  &--right {
    top: 0;
    right: 0;
    bottom: 0;
    width: 40vw;
    background: radial-gradient(
      ellipse at 100% 50%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(3.12rem);
    animation: rightGlow 10s ease-in-out infinite alternate;
  }

  &--bottom {
    bottom: 0;
    left: 0;
    right: 0;
    height: 40vh;
    background: radial-gradient(
      ellipse at 50% 100%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(3.12rem);
    animation: bottomGlow 14s ease-in-out infinite alternate;
  }

  &--left {
    top: 0;
    left: 0;
    bottom: 0;
    width: 40vw;
    background: radial-gradient(
      ellipse at 0% 50%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(3.12rem);
    animation: leftGlow 11s ease-in-out infinite alternate;
  }
}

.background__corner-gradient {
  &--top-left {
    top: 0;
    left: 0;
    width: 50vh;
    height: 50vh;
    background: radial-gradient(
      circle at 0% 0%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(2.81rem);
    animation: cornerTL 16s ease-in-out infinite alternate;
  }

  &--top-right {
    top: 0;
    right: 0;
    width: 50vh;
    height: 50vh;
    background: radial-gradient(
      circle at 100% 0%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(2.81rem);
    animation: cornerTR 15s ease-in-out infinite alternate;
  }

  &--bottom-left {
    bottom: 0;
    left: 0;
    width: 50vh;
    height: 50vh;
    background: radial-gradient(
      circle at 0% 100%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(2.81rem);
    animation: cornerBL 13s ease-in-out infinite alternate;
  }

  &--bottom-right {
    bottom: 0;
    right: 0;
    width: 50vh;
    height: 50vh;
    background: radial-gradient(
      circle at 100% 100%,
      rgba(70, 200, 255, 0.7) 0%,
      rgba(70, 200, 255, 0.3) 30%,
      rgba(70, 200, 255, 0.1) 50%,
      transparent 80%
    );
    filter: blur(2.81rem);
    animation: cornerBR 14s ease-in-out infinite alternate;
  }
}

/* ========== BACKGROUND LAYERS ========== */

.background__layer {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;

  &--honeycomb {
    background-image: url(@/assets/svg/background.svg);
    background-size: cover;
    z-index: 1;
  }

  &--cursor-gradient {
    width: 31.25rem;
    height: 31.25rem;
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
}

.background__content {
  position: relative;
  z-index: 100;
  pointer-events: auto;
}

/* ========== ANIMATIONS ========== */

@keyframes topGlow {
  0% {
    opacity: 0.4;
    filter: blur(2.81rem) brightness(0.8);
    transform: translateY(-5%);
  }
  100% {
    opacity: 0.8;
    filter: blur(60px) brightness(1.3);
    transform: translateY(0);
  }
}

@keyframes rightGlow {
  0% {
    opacity: 0.4;
    filter: blur(2.81rem) brightness(0.8);
    transform: translateX(5%);
  }
  100% {
    opacity: 0.8;
    filter: blur(60px) brightness(1.3);
    transform: translateX(0);
  }
}

@keyframes bottomGlow {
  0% {
    opacity: 0.4;
    filter: blur(2.81rem) brightness(0.8);
    transform: translateY(5%);
  }
  100% {
    opacity: 0.8;
    filter: blur(60px) brightness(1.3);
    transform: translateY(0);
  }
}

@keyframes leftGlow {
  0% {
    opacity: 0.4;
    filter: blur(2.81rem) brightness(0.8);
    transform: translateX(-5%);
  }
  100% {
    opacity: 0.8;
    filter: blur(60px) brightness(1.3);
    transform: translateX(0);
  }
}

@keyframes cornerTL {
  0% {
    opacity: 0.3;
    filter: blur(40px) brightness(0.8);
    transform: scale(0.9) translate(-5%, -5%);
  }
  100% {
    opacity: 0.7;
    filter: blur(55px) brightness(1.4);
    transform: scale(1.2) translate(0, 0);
  }
}

@keyframes cornerTR {
  0% {
    opacity: 0.3;
    filter: blur(40px) brightness(0.8);
    transform: scale(0.9) translate(5%, -5%);
  }
  100% {
    opacity: 0.7;
    filter: blur(55px) brightness(1.4);
    transform: scale(1.2) translate(0, 0);
  }
}

@keyframes cornerBL {
  0% {
    opacity: 0.3;
    filter: blur(40px) brightness(0.8);
    transform: scale(0.9) translate(-5%, 5%);
  }
  100% {
    opacity: 0.7;
    filter: blur(55px) brightness(1.4);
    transform: scale(1.2) translate(0, 0);
  }
}

@keyframes cornerBR {
  0% {
    opacity: 0.3;
    filter: blur(40px) brightness(0.8);
    transform: scale(0.9) translate(5%, 5%);
  }
  100% {
    opacity: 0.7;
    filter: blur(55px) brightness(1.4);
    transform: scale(1.2) translate(0, 0);
  }
}

@include down($lg) {
  .background__edge-gradient {
    filter: blur(2.18rem);
    
    &--left,
    &--right {
      width: 60vw;
    }
    
    &--top,
    &--bottom {
      height: 30vh;
    }
  }
  
  .background__corner-gradient {
    width: 70vw;
    height: 70vw;
    filter: blur(1.87rem);
  }
  
  .background__layer {
    &--cursor-gradient {
      display: none;
    }
  }
}
</style>