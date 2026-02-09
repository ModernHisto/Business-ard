<script setup>
import { RouterLink, RouterView } from 'vue-router'
import GradientCursor from '@/components/GradientCursor.vue'
import TheHeader from '@/layout/Header.vue';
import TheFooter from '@/layout/Footer.vue';
</script>

<template>
  <GradientCursor>
    <TheHeader />
    <router-view v-slot="{ Component }">
      <transition name="route" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
    <TheFooter />
  </GradientCursor>
</template>

<style lang="scss">
.content-layer>section {
  @include up($md) {
    height: calc(100vh - 3.8rem);
  }
}
</style>