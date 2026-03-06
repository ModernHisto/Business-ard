<script setup>
import BacklightControl from '@/components/header/BacklightControl.vue';
</script>

<template>
  <div class="header__ledge" aria-hidden="true">
    <svg xmlns="http://www.w3.org/2000/svg" height="100%" width="100%" viewBox="-4.01 -2.01 8.02 3.02">
      <path d="M-100 0-3 0-2 1 2 1 3 0 100 0" stroke="#ffffff1c" stroke-width="0.05" fill="rgba(29, 29, 29, 0.396)" />
      <path d="M-100 0-100-2 100-2 100 0" fill="transparent" />
    </svg>
    <BacklightControl />
  </div>
</template>

<style lang="scss" scoped>
.header__ledge {
  position: absolute;
  z-index: 999;
  left: 50%;
  top: -184%;
  transform: translateX(-50%) translateY(100%);
  width: 100%;
  height: 6.5rem;

  >svg {
    filter: drop-shadow(0px 3px 1px #00000058);
  }

  &::after {
    content: "";
    z-index: 998;
    display: block;
    position: relative;
    left: calc(50% - 6.6rem);
    bottom: 42%;
    width: 13.3rem;
    height: 2.3rem;
    clip-path: polygon(18% 0, 83% 0, 100% 100%, 0% 100%);
    backdrop-filter: blur(7px);
    -webkit-backdrop-filter: blur(7px);
    rotate: 180deg;
  }
}
</style>