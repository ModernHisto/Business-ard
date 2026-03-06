<script setup>
import CleanCenter from '@/assets/svg/backlight_control/cleanCenter.vue';
import DiagonalStripes from '@/assets/svg/backlight_control/diagonalStripes.vue';
import SlidingStrips from '@/assets/svg/backlight_control/slidingStrips.vue';
</script>

<template> 
<div class="backlight-control">
    <div class="backlight-control__container">
      <SlidingStrips />
      <CleanCenter />
      <DiagonalStripes />
    </div>
  </div>
</template>

<style lang="scss">
.backlight-control {
  &__container {
    z-index: 1000;
    position: absolute;
        bottom: 8%;
    left: calc(50% - 8.03rem);
    width: 16.1rem;
    height: 27px;
    display: flex;
    gap: 0.5rem;
    justify-content: center;

    .svg-container {
      transition: color 0.3s ease;
      color: $translucent-white;
      stroke: $translucent-white;
      height: 100%;
      width: max-content;
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
  }
}

</style>