<script setup>
import icon from '@/components/home/Icon.vue'
import mainButton from '@/components/reusable/buttons/MainButton.vue';
</script>

<template>
  <section class="home">
    <v-container>
      <div class="home__container">
        <div class="home__content">
          <p class="home__greeting h3">Hi, I'm Daniil</p>

          <p class="home__subtitle h1">Designing Dreams, <br> Developing Realities</p>

          <p class="home__description">
            I write clean, maintainable code, stay current with current trends, and always strive for the best user
            experience.

            Here you'll find my projects, the technologies I work with, and learn a little about my thinking and
            problem-solving skills. I'm ready to discuss collaboration, interesting challenges, or just chat about the
            web!

            Welcome to my digital world.
          </p>
          <main-button class="home__button" />
        </div>
        <div class="home__icon">
          <a href="https://github.com/ModernHisto" target="_blank" rel="noopener noreferrer">
          <icon class="home__icon-item" />
          </a>
        </div>
      </div>
    </v-container>
  </section>
</template>

<style lang="scss">
.home {
  &__container {
    padding-top: 10rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    width: 90rem;
    gap: 2rem;

    @include down($lg) {
      flex-direction: column;
      align-items: center;
      padding-top: 1rem 0;
    }

    @include down($md) {
      padding: 1rem 0;
    }
  }

  &__icon {
    width: 38%;

    @include down($md) {
      width: 60%;
    }
     @include down($sm) {
      width: 85%;
    }
  }

  &__content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 50%;

    @include down($lg) {
      order: 1;
      text-align: center;
      align-items: center;
      width: 100%;
    }
  }

  &__greeting {
    color: $green;
    width: 100%;
  }

  &__subtitle {
    margin: 1.5rem 0;
  }

  &__description {
    line-height: 1.688rem;
    margin-bottom: 2.5rem;
  }
}
</style>