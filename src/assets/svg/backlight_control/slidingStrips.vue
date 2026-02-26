<template>
  <div class="svg-container">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="-1.007 -0.00499988 11.01 7.007">
      <path
        d="M.985.996 7.996.998C8.536 1.006 9.001 1.456 9.002 2.003L8.999 5.009C9.003 5.518 8.499 5.993 7.999 5.993L1.006 6.002C.504 6 .004 5.599.004 5.012L-.007 2.008C.003 1.465.502.999.984.996"
        stroke="#525252" stroke-width="0.3" fill="none" />

      <path d="M3.501 1.998 4.494 2.003 5.5 5 4.504 4.999 3.501 1.999" stroke="#525252" stroke-width="0.3"
        fill="none" />
      <path d="M6 2 7 2 8 5 7 5 6 2" stroke="#525252" stroke-width="0.3" fill="none" />
      <path d="M2 2 3 5 2 5 1 2 2 2" stroke="#525252" stroke-width="0.3" fill="none" />

    </svg>
  </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.svg-container {
  transition: color 0.3s ease;
  color: $translucent-white;
  stroke: $translucent-white;
  height: 2.5rem;
  width: 3.5rem;
}

@include up($md) {
  .svg-container:hover {
    filter: drop-shadow(0 0 1px $green);
    color: $light-green;
  }
}

.svg-container:hover {
  svg {
    path {
      stroke: $translucent-white !important;
    }
  }
}

.svg-container:active {
  svg {
    filter: drop-shadow(0 0 1px $green);
    color: $green;
    color: #b2fa883a;
  }
}
</style>