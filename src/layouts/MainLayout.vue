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
          <a href="#activities" class="menu-link">Виды деятельности</a>
          <a href="#podcasts" class="menu-link">Подкасты</a>
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
  padding: 0 24px;
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
  height: 40px;
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
</style>
