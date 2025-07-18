<template>
  <v-app>
    <div class="layout-main">
      <the-header />
      <v-main>
        <router-view v-slot="{ Component }">
          <transition name="route" mode="out-in">
            <component :is="Component" />
          </transition>
        </router-view>
      </v-main>
      <the-footer />
    </div>
  </v-app>
</template>

<script setup>
import TheHeader from '@/layout/the-header.vue';
import TheFooter from '@/layout/the-footer.vue';
</script>

<style lang="scss">
.layout-main {
  padding: px2vw(240, $lg) 0 0 0;

  @include up($lg) {
    padding: px2vw(60, $lg) 0 0 0;
  }
}
</style>
