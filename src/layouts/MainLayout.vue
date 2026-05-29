<template>
  <q-layout view="lHh Lpr lFf">
    <!-- Хедер -->
    <q-header class="header">
      <q-toolbar class="container">
        <!-- Логотип слева -->
        <q-toolbar-title class="logo">
          <router-link to="/" class="logo-link">
            <img src="~assets/logo.svg" alt="Логотип" class="logo-img" />
          </router-link>
        </q-toolbar-title>

        <!-- Меню справа для десктопа -->
        <div class="desktop-menu q-gutter-md">
          <router-link to="/" class="menu-link" active-class="menu-link-active"
            >Главная</router-link
          >
          <a href="#activities" class="menu-link" @click.prevent="scrollTo('activities')"
            >Виды деятельности</a
          >
          <router-link to="/podcasts" class="menu-link">Подкасты</router-link>
          <!-- <a href="#podcasts" class="menu-link">Подкасты</a> -->
          <a
            href="https://school-portal.ru"
            target="_blank"
            rel="noopener noreferrer"
            class="menu-link"
            >Школьный портал</a
          >
        </div>

        <!-- Мобильное меню (гамбургер) -->
        <q-btn
          v-if="$q.screen.lt.md"
          flat
          round
          dense
          icon="menu"
          class="menu-btn"
          @click="mobileMenuOpen = !mobileMenuOpen"
        />
      </q-toolbar>

      <!-- Выпадающее меню для мобильных -->
      <q-drawer
        v-model="mobileMenuOpen"
        side="right"
        overlay
        bordered
        :width="250"
        class="mobile-drawer"
      >
        <q-list>
          <q-item clickable v-close-popup to="/">
            <q-item-section>Главная</q-item-section>
          </q-item>
          <q-item clickable v-close-popup @click="scrollTo('activities')">
            <q-item-section>Виды деятельности</q-item-section>
          </q-item>
          <q-item clickable v-close-popup @click="scrollTo('podcasts')">
            <q-item-section>Подкасты</q-item-section>
          </q-item>
          <q-item clickable v-close-popup @click="openExternalLink('https://school-portal.ru')">
            <q-item-section>Школьный портал</q-item-section>
          </q-item>
        </q-list>
      </q-drawer>
    </q-header>

    <!-- Основной контент -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <q-page-sticky position="bottom-right" :offset="[60, 60]">
      <q-btn round color="#FBE1BA" @click="scrollToTop"
        ><q-img src="~assets/Button_icon.svg" class="btn-icon" fit="contain"
      /></q-btn>
    </q-page-sticky>
    <!-- Футер -->
    <div class="footer-section" :class="{ 'podcasts-footer': $route.path === '/podcasts' }">
      <div class="footer-container">
        <div class="footer-grid">
          <!-- Колонка 1: Логотип -->
          <div class="footer-col">
            <div class="footer-logo">
              <img src="~assets/logo.svg" alt="Логотип" class="footer-logo-img" />
            </div>
            <div class="footer-logo-text">
              © 2026 Муниципальное автономное общеобразовательное учреждение «Средняя
              общеобразовательная школа «Мастерград» города Перми
            </div>
          </div>

          <!-- Колонка 2: Ссылки -->
          <div class="footer-col">
            <div class="footer-links">
              <a href="/" class="footer-link">Главная</a>
              <a href="#podcasts" class="footer-link">Подкасты</a>
              <a href="#activities" class="footer-link">Школьный портал</a>
            </div>
          </div>

          <!-- Колонка 3: Ссылки -->
          <div class="footer-col">
            <div class="footer-links">
              <a href="/about" class="footer-link">Учебная деятельность</a>
              <a href="/contacts" class="footer-link">Внеурочная деятельность</a>
              <a href="/privacy" class="footer-link">Дополнительное образование</a>
            </div>
          </div>

          <!-- Колонка 4: Соцсети -->
          <div class="footer-col footer-col-right">
            <div class="footer-title">Контакты</div>
            <div class="footer-addres">
              Адрес: 614000, Пермский край, город Пермь, Сибирская ул., д. 17
            </div>
            <div class="footer-addres">8 (347) 212-70-50</div>
            <div class="footer-addres">do@perm.permkrai.ru</div>
            <div class="footer-social">
              <a
                href="https://maximum.ru"
                target="_blank"
                rel="noopener noreferrer"
                class="social-link"
              >
                <q-img src="~assets/max-icon.svg" class="social-icon" fit="contain" />
              </a>
              <a
                href="https://vk.com"
                target="_blank"
                rel="noopener noreferrer"
                class="social-link"
              >
                <q-img src="~assets/vk-icon.svg" class="social-icon" fit="contain" />
              </a>
            </div>
          </div>
        </div>

        <!-- Нижняя строка с копирайтом -->
        <div class="footer-partners">
          <div class="footer-bottom">
            <div class="footer-partner-text">Сделано в:</div>
            <q-img src="~assets/souz.svg" class="partner-1" fit="contain" />
            <q-img src="~assets/sot.svg" class="partner-2" fit="contain" />
          </div>
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useQuasar } from 'quasar';

const $q = useQuasar();
const mobileMenuOpen = ref(false);

// Функция для плавного скролла к секции на текущей странице
const scrollTo = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' });
  }
  mobileMenuOpen.value = false;
};

// Открытие внешней ссылки
const openExternalLink = (url) => {
  window.open(url, '_blank', 'noopener,noreferrer');
};

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth',
  });
};
</script>

<style scoped lang="scss">
.header {
  background-color: white !important;
  box-shadow: none !important; // убираем тень
  border-bottom: none !important;
  color: #131314;
  padding: 8px 0;
}

.container {
  max-width: 1600px;
  width: 100%;
  margin: 0 auto;
}

.logo {
  padding: 0;
}

.logo-link {
  display: flex;
  align-items: center;
  gap: 12px;
  text-decoration: none;
  color: #131314;
}

.logo-img {
  height: 80px;
  width: auto;
}

.logo-text {
  font-family: 'Mulish', sans-serif;
  font-weight: 700;
  font-size: 20px;
  color: #131314;
}

.desktop-menu {
  display: flex;
  gap: 32px;
}

.menu-link {
  font-family: 'Mulish', sans-serif;
  font-weight: 400;
  font-size: 20px;
  color: #131314;
  text-decoration: none;
  transition: opacity 0.2s ease;
  cursor: pointer;
  background: none;
  border: none;
  padding: 0;
}

.menu-link:hover {
  opacity: 0.7;
}

.menu-link-active {
  padding-bottom: 4px;
}

.menu-btn {
  color: #131314;
}

// Футер
.footer-section {
  background: #ffffff;
  padding: 60px 24px 30px;
  margin-top: 60px;
}

.podcasts-footer {
  background: #dce0f4; // Цвет, как у секции подкастов
  border-radius: 100px 100px 0px 0px;
}

.footer-container {
  max-width: 1600px;
  margin: 0 auto;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
  margin-bottom: 50px;
}

.footer-col {
  display: flex;
  flex-direction: column;
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: 12px;
}

.footer-logo-img {
  height: 100px;
  width: auto;
}

.footer-logo-text {
  font-family: 'Mulish', sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #4b5563;
  line-height: 40px;
  max-width: 350px;
}

.footer-links {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.footer-link {
  font-family: 'Mulish', sans-serif;
  font-size: 20px;
  font-weight: 400;
  color: #131314;
  text-decoration: none;
  transition: color 0.3s ease;

  &:hover {
    color: #ffffff;
  }
}

.footer-social {
  display: flex;
  flex-direction: row; // Иконки в одну строку
  gap: 12px;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 12px;
  font-family: 'Mulish', sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #c4c4c4;
  text-decoration: none;
  transition: color 0.3s ease;

  &:hover {
    color: #ffffff;
  }
}

.social-icon {
  width: 40px;
  height: 40px;
  margin-top: 10px;
}
.footer-partners {
  border-top: 1px solid #dce0f4;
}
.footer-bottom {
  max-width: 350px;
  padding-top: 30px;
  display: flex;
  justify-content: center !important;
  gap: 8px;
  align-items: center;
  margin: 0 auto;
}
.footer-partner-text {
  width: 85px;
  font-family: 'Mulish', sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #8f8f9a;
}

.footer-col-right {
  text-align: right;
  align-items: flex-end;
}

.footer-title {
  font-family: Mulish;
  font-weight: 700;
  font-size: 28px;
  color: #505468;
  margin-bottom: 16px;
}

.footer-addres {
  font-family: Mulish;
  font-weight: 400;
  font-size: 16px;
  color: #4b5563;
  padding-bottom: 6px;
}

.partner-1 {
  width: 170px;
  height: auto;
}

.partner-2 {
  width: 68px;
  height: 40px;
  margin-left: 8px;
}
// Адаптив для планшетов
@media (max-width: 1024px) {
  .footer-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 40px;
  }
}

// Мобильные стили
@media (max-width: 1023px) {
  .desktop-menu {
    display: none;
  }
}

@media (min-width: 1024px) {
  .menu-btn {
    display: none;
  }
}

.mobile-drawer {
  background: white;
  .q-item {
    font-family: 'Mulish', sans-serif;
    font-weight: 600;
    color: #131314;
  }
}

// Адаптив для мобильных
@media (max-width: 768px) {
  .logo-img {
    height: 55px;
    width: auto;
  }
  .footer-section {
    padding: 50px 20px 25px;
  }

  .footer-grid {
    grid-template-columns: 1fr;
    gap: 35px;
  }

  .footer-logo {
    justify-content: center;
  }

  .footer-links {
    align-items: center;
    text-align: center;
  }

  .footer-social {
    align-items: center;
  }
}
</style>
