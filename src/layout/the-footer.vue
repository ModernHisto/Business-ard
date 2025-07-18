<template>
  <footer class="the-footer">
    <v-container>
      <!-- mobile -->
      <div class="the-footer__content --mobile d-lg-none">
        <div class="the-footer__contacts text-center d-flex flex-column">
          <div class="size-2 color-dark-50">Поможем вам с выбором бизнес-центра</div>
          <div class="h4">sales@solo-group.ru</div>
          <div class="size-2">+7 (812) 622-00-99</div>
        </div>

        <div>
          <div class="the-footer__logo">
            <logo />
          </div>


          <div class="the-footer__nav size-1">
            <ul class="the-footer__nav-links d-flex flex-column">
              <router-link v-for="link in navLinks" :to="link.to">
                <li class="d-flex justify-space-between align-center">
                  {{ link.name }}
                  <arrow />
                </li>
              </router-link>
            </ul>


            <div class="the-footer__nav-docs d-flex flex-column color-dark-50">
              <router-link to="#">Политика конфиденциальности</router-link>
              <router-link to="#">Пользовательское соглашение</router-link>
            </div>
          </div>
        </div>

        <div class="the-footer__copyright d-flex flex-column justify-start color-dark-50 size-2">
          <div>199004, г. Санкт-Петербург, Средний проспект <br>36/40. Бизнес-центр «Остров»</div>
          <div>Copyright © SOLO ГРУПП 2025</div>
        </div>
      </div>


      <!-- desktop -->
      <div class="the-footer__content --desktop d-none">
        <div class="d-flex flex-column justify-end">
          <div class="the-footer__logo">
            <logo />
          </div>

          <div class="the-footer__copyright d-flex flex-column justify-start color-dark-50 size-2">
            <div>199004, г. Санкт-Петербург, <br>Средний проспект 36/40. <br>Бизнес-центр «Остров»</div>
            <div>Copyright © SOLO ГРУПП 2025</div>
          </div>
        </div>

        <div class="">
          <div class="the-footer__contacts text-start d-flex flex-column">
            <div class="size-2 color-dark-50">Поможем вам с выбором бизнес-центра</div>
            <div class="h4">sales@solo-group.ru</div>
            <div class="size-2">+7 (812) 622-00-99</div>
          </div>

          <div class="the-footer__nav size-1">
            <ul class="the-footer__nav-links d-flex flex-column">
              <router-link v-for="link in navLinks" :to="link.to">
                <li class="d-flex justify-space-between align-center">
                  {{ link.name }}
                  <arrow />
                </li>
              </router-link>
            </ul>

            <div class="the-footer__nav-docs d-flex flex-column color-dark-50">
              <router-link to="/">Политика конфиденциальности</router-link>
              <router-link to="/">Пользовательское соглашение</router-link>
            </div>
          </div>
        </div>
      </div>
    </v-container>
  </footer>
</template>

<script setup>
import logo from '../assets/svg/logo.vue'
import arrow from '../assets/svg/arrow.vue'

const navLinks = [
  {
    name: 'Компания',
    to: { name: 'company' },
  },
  {
    name: 'Аренда',
    to: { name: 'office-rentals' },
  },
  {
    name: 'Проекты',
    to: { name: 'projects' },
  },
  {
    name: 'Контакты',
    to: { name: 'contacts' },
  },
]
</script>

<style lang="scss">
.the-footer {
  
}
</style>