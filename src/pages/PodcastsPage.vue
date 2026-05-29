<template>
  <q-page padding>
    <!-- Секция "Подкасты" -->
    <div id="podcasts" class="podcasts-section">
      <div class="podcasts-container">
        <router-link to="/" class="menu-link-bred" active-class="menu-link-active"
          >Главная</router-link
        ><a class="menu-link-bred">/</a>
        <a class="menu-link-bred">Подкасты</a>
        <div class="podcasts-title">Подкасты</div>
        <div class="podcasts-description">
          Разнообразные образовательные программы для всестороннего развития каждого ученика
        </div>

        <!-- Сетка карточек подкастов -->
        <div class="podcasts-grid">
          <div v-for="(podcast, index) in visiblePodcasts" :key="index" class="podcast-card">
            <div class="podcast-image">
              <q-img
                src="~assets/video.svg"
                class="podcast-img"
                fit="cover"
                :no-native-menu="true"
              />
              <div class="play-button" @click="playPodcast(podcast)">
                <q-img src="~assets/play-icon.svg" class="play-icon" fit="contain" />
              </div>
            </div>
            <div class="podcast-title">{{ podcast.title }}</div>
            <!-- <div class="podcast-author">{{ podcast.author }}</div> -->
          </div>
        </div>

        <!-- Кнопка "Показать больше" -->
        <div v-if="hasMorePodcasts" class="show-more-wrapper">
          <q-btn
            unelevated
            class="show-more-btn"
            no-caps
            :loading="loadingMore"
            @click="loadMorePodcasts"
          >
            <span class="btn-content">
              Показать больше
              <q-img src="~assets/arrow-down.svg" class="btn-icon" fit="contain" />
            </span>
          </q-btn>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { useQuasar } from 'quasar';

const $q = useQuasar();

const loadingMore = ref(false);

// Данные подкастов
const allPodcasts = ref([
  {
    title: 'Как выбрать профессию?',
    author: 'Елена Смирнова',
    duration: '24 мин',
    image: '~assets/podcast-1.jpg',
  },
  {
    title: 'IT-сфера: мифы и реальность',
    author: 'Алексей Иванов',
    duration: '32 мин',
    image: '~assets/podcast-2.jpg',
  },
  {
    title: 'Профессия будущего',
    author: 'Мария Петрова',
    duration: '28 мин',
    image: '~assets/podcast-3.jpg',
  },
  {
    title: 'Как стать инженером?',
    author: 'Дмитрий Сидоров',
    duration: '35 мин',
    image: '~assets/podcast-4.jpg',
  },
  {
    title: 'Творческие профессии',
    author: 'Анна Козлова',
    duration: '22 мин',
    image: '~assets/podcast-5.jpg',
  },
  {
    title: 'Медицина сегодня',
    author: 'Татьяна Морозова',
    duration: '30 мин',
    image: '~assets/podcast-6.jpg',
  },
  {
    title: 'Бизнес и стартапы',
    author: 'Павел Новиков',
    duration: '40 мин',
    image: '~assets/podcast-7.jpg',
  },
  {
    title: 'Педагогика нового времени',
    author: 'Ольга Соколова',
    duration: '26 мин',
    image: '~assets/podcast-8.jpg',
  },
  {
    title: 'Экология и устойчивое развитие',
    author: 'Игорь Васильев',
    duration: '33 мин',
    image: '~assets/podcast-9.jpg',
  },
]);

// Количество подкастов для отображения (начальные 6 = 2 ряда по 3)
const visibleCount = ref(6);

// Видимые подкасты
const visiblePodcasts = computed(() => {
  return allPodcasts.value.slice(0, visibleCount.value);
});

// Есть ли ещё подкасты для показа
const hasMorePodcasts = computed(() => {
  return visibleCount.value < allPodcasts.value.length;
});

// Загрузка дополнительных подкастов
const loadMorePodcasts = () => {
  loadingMore.value = true;

  // Имитация загрузки (можно убрать или оставить для эффекта)
  setTimeout(() => {
    visibleCount.value = allPodcasts.value.length;
    loadingMore.value = false;

    $q.notify({
      message: 'Все подкасты загружены',
      color: 'positive',
      position: 'bottom',
      timeout: 2000,
    });
  }, 500);
};

const onLearnMore = () => {
  $q.notify({
    message: 'Здесь будет дополнительная информация',
    color: 'primary',
    position: 'top',
    icon: 'info',
  });
};
// Функция для воспроизведения подкаста
const playPodcast = (podcast: any) => {
  // Здесь можно открыть модальное окно с видео или перейти на страницу подкаста
  $q.notify({
    message: `Воспроизведение: ${podcast.title}`,
    color: 'info',
    position: 'top',
    icon: 'play_circle',
    timeout: 2000,
  });

  // Пример открытия модального окна с видео:
  $q.dialog({
    title: podcast.title,
    message: 'Здесь будет видео плеер',
    persistent: true,
    ok: 'Закрыть',
  });
};
</script>

<style scoped lang="scss">
.menu-link-bred {
  font-family: 'Mulish', sans-serif;
  font-weight: 400;
  font-size: 16px;
  color: #131314;
  text-decoration: none;
  transition: opacity 0.2s ease;
  cursor: pointer;
  background: none;
  border: none;
  padding: 0;
  padding-right: 12px;
}

.menu-link-active {
  color: #505468;
}
// Секция "Подкасты"
.podcasts-section {
  padding: 80px 24px 100px;
  margin: 0 auto;
}

.podcasts-container {
  max-width: 1600px;
  margin: 0 auto;
}

.podcasts-title {
  font-family: 'Mulish', sans-serif;
  font-size: 80px;
  font-weight: 700;
  color: #505468;
  text-align: center;
  margin-bottom: 24px;
}

.podcasts-description {
  font-family: 'Mulish', sans-serif;
  font-size: 24px;
  font-weight: 400;
  color: #4b5563;
  text-align: center;
  max-width: 800px;
  margin: 0 auto 60px;
  line-height: 1.5;
}

.podcasts-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
  margin-bottom: 40px;
}

.podcast-card {
  cursor: pointer;
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-8px);
  }
}

.podcast-image {
  position: relative;
  border-radius: 24px;
  overflow: hidden;
  margin-bottom: 16px;
  aspect-ratio: 16 / 9;
  cursor: pointer;

  &:hover .play-button {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1.1);
  }
}

.podcast-img {
  width: 100%;
  height: 100%;
  transition: transform 0.3s ease;

  :deep(.q-img__image) {
    object-fit: cover;
  }
}

.podcast-image:hover .podcast-img {
  transform: scale(1.05);
}

.play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 60px;
  height: 60px;
  backdrop-filter: blur(4px);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  opacity: 0.9;

  &:hover {
    transform: translate(-50%, -50%) scale(1.1);
  }
}

.play-icon {
  width: 60px;
  height: 60px;
}

.podcast-title {
  font-family: 'Mulish', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: #4b5563;
}

.show-more-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 64px;
}

.show-more-btn {
  background: #fbe1ba;
  color: #6f552e;
  font-family: 'Mulish', sans-serif;
  font-size: 24px;
  font-weight: 400;
  padding: 12px 40px;
  border-radius: 40px;
  transition: all 0.3s ease;

  &:hover {
    background: #e8e8e8;
    transform: translateY(-2px);
  }
}

.btn-content {
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.btn-icon {
  width: 24px;
  height: 24px;

  transition: transform 0.3s ease;
}

.show-more-btn:hover .btn-icon {
  transform: translateX(4px);
}

// Адаптив для планшетов
@media (max-width: 1024px) {
  .podcasts-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }

  .podcasts-title {
    font-size: 60px;
  }
}

// Адаптив для мобильных
@media (max-width: 768px) {
  .podcasts-section {
    padding: 60px 20px 80px;
  }

  .podcasts-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .podcasts-title {
    font-size: 48px;
  }

  .podcasts-description {
    font-size: 16px;
    margin-bottom: 40px;
  }
}

@media (max-width: 480px) {
  .podcasts-title {
    font-size: 36px;
  }

  .show-more-btn {
    padding: 10px 30px;
    font-size: 14px;
  }
}
</style>
