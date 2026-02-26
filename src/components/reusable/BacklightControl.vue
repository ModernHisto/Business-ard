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

</style>