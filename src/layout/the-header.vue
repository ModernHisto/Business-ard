<script setup>
import logo from '../assets/svg/logo.vue';
import arrow from '../assets/svg/arrow.vue';
import { useStore } from "vuex";
import { computed } from "vue";
import feedbackModal from "../components/reusable/feedback/feedback-modal.vue";

const store = useStore();

const isMenuOpened = computed(() => store.state.isMenuOpened);
const setMenuOpened = () => {
  store.commit('setMenuOpened');
}

</script>

<template>
  <header class="the-header">
    <div class="the-header__content size-3">
      <div class="the-header__logo">
        <logo />
      </div>

      <div class="the-header__contacts">
        <address class="the-header__address">
          <a href="tel:+78126220099" class="the-header__contact-link">+7 (812) 622-00-99</a>
          <a href="mailto:sales@solo-group.ru" class="the-header__contact-link">sales@solo-group.ru</a>
        </address>
      </div>

      <nav class="the-header__navigation">
        <ul class="the-header__nav-list">
          <RouterLink :to="{ name: 'company' }" class="the-header__nav-link">
            <li class="the-header__nav-item">
              Компания
            </li>
          </RouterLink>
          <RouterLink :to="{ name: 'office-rentals' }" class="the-header__nav-link">
            <li class="the-header__nav-item">
              Аренда
            </li>
          </RouterLink>
          <RouterLink :to="{ name: 'projects' }" class="the-header__nav-link">
            <li class="the-header__nav-item">
              Проекты
            </li>
          </RouterLink>
          <RouterLink :to="{ name: 'contacts' }" class="the-header__nav-link">
            <li class="the-header__nav-item">
              Контакты
            </li>
          </RouterLink>
        </ul>
      </nav>
      <div class="the-header__button d-none d-lg-block">
        <feedback-modal />
      </div>

      <button @click="setMenuOpened" class="the-header__burger"></button>

      <Transition name="slide-down">
        <div v-if="isMenuOpened" class="the-header__mobile-menu">

          <div class="the-header__mobile-navigation">
            <ul class="the-header__mobile-nav-list">
              <RouterLink :to="{ name: 'company' }" class="the-header__mobile-nav-link">
                <li @click="setMenuOpened" class="the-header__mobile-nav-item">
                  Компания
                  <arrow />
                </li>
              </RouterLink>
              <RouterLink :to="{ name: 'office-rentals' }" class="the-header__mobile-nav-link">
                <li @click="setMenuOpened" class="the-header__mobile-nav-item">
                  Аренда
                  <arrow />
                </li>
              </RouterLink>
              <RouterLink :to="{ name: 'projects' }" class="the-header__mobile-nav-link">
                <li @click="setMenuOpened" class="the-header__mobile-nav-item">
                  Проекты
                  <arrow />
                </li>
              </RouterLink>
              <RouterLink :to="{ name: 'contacts' }" class="the-header__mobile-nav-link">
                <li @click="setMenuOpened" class="the-header__mobile-nav-item">
                  Контакты
                  <arrow />
                </li>
              </RouterLink>
            </ul>
          </div>

          <div class="the-header__documents">
            <RouterLink to="/" class="the-header__document-link">Политика конфиденциальности</RouterLink>
            <RouterLink to="/" class="the-header__document-link">Пользовательское соглашение</RouterLink>
          </div>

          <address class="the-header__mobile-address">
            <a href="tel:+78126220099" class="the-header__mobile-contact-link">+7 (812) 622-00-99</a>
            <a href="mailto:sales@solo-group.ru" class="the-header__mobile-contact-link">sales@solo-group.ru</a>
          </address>

          <div class="the-header__mobile-button">
            <feedback-modal class="d-lg-none" />
          </div>

          <div class="the-header__company-details color-dark-20 size-1">
            <div>199004, г. Санкт-Петербург, Средний проспект 36/40. Бизнес-центр «Остров»</div>
            <div>Copyright © SOLO ГРУПП 2025</div>
          </div>
        </div>
      </Transition>

    </div>
  </header>
</template>

<style lang="scss">
.the-header {
  
}

/* Анимация появления */
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.4s ease;
  transform-origin: top center;
}

.slide-down-enter-from,
.slide-down-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}

.slide-down-enter-to,
.slide-down-leave-from {
  transform: translateY(0);
  opacity: 1;
}
</style>