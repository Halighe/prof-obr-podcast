<template>
  <q-page>
    <!-- Hero секция (вне q-card, на всю ширину) -->
    <div class="hero-section">
      <!-- Фоновое изображение через q-img -->
      <q-img src="~assets/orig 1.svg" class="hero-bg" fit="cover" :no-native-menu="true">
        <!-- Затемнение (опционально) -->
      </q-img>

      <!-- Контент поверх фона -->
      <div class="hero-content-wrapper">
        <div class="hero-content">
          <q-img
            src="~assets/png.svg"
            class="hero-center-img"
            fit="contain"
            :no-native-menu="true"
            :no-spinner="false"
          />
          <div class="hero-topic-wrapper">
            <div class="hero-topic">Профориентация школьников</div>
            <div class="hero-text">
              демонстрация возможностей школы, систематизация и представление информации
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Основной контент в q-card -->
    <div class="main-content-wrapper">
      <q-card class="main-card" flat bordered>
        <q-card-section>
          <!-- Блок "Пространство для детей, родителей и педагогов" с фоновой картинкой -->
          <div class="space-section">
            <!-- Фоновая картинка на всю ширину -->
            <div class="space-bg"></div>

            <div class="space-content-wrapper">
              <div class="space-content">
                <!-- Картинка слева -->
                <div class="space-image">
                  <picture>
                    <source media="(max-width: 480px)" srcset="~assets/Frame2131330347.svg" />
                    <source media="(max-width: 768px)" srcset="~assets/mobile-image.svg" />
                    <source media="(min-width: 769px)" srcset="~assets/Frame2131330347.svg" />
                    <img
                      src="~assets/Frame2131330347.svg"
                      class="space-img"
                      alt="Пространство для детей, родителей и педагогов"
                    />
                  </picture>
                </div>

                <!-- Текст по левому краю -->
                <div class="space-text">
                  <div class="space-title">Пространство для детей, родителей и педагогов</div>
                  <div class="space-description">
                    Повышение информированности о существующих программах, проектах и мероприятиях,
                    направленных на профессиональное самоопределение.
                  </div>
                </div>
              </div>
              <!-- Блок с преимуществами -->
              <div class="advantages-section">
                <div class="row q-col-gutter-lg">
                  <!-- Первая колонка: картинка сверху, текст снизу -->
                  <div class="col-12 col-md-6">
                    <div class="advantage-card">
                      <div class="advantage-image">
                        <q-img
                          src="~assets/Vector.svg"
                          class="advantage-img"
                          fit="contain"
                          :no-native-menu="true"
                        />
                      </div>
                      <div class="advantage-description">
                        Обеспечение лёгкого доступа к актуальной информации о возможностях развития
                        в рамках учебной, внеурочной и дополнительной деятельности
                      </div>
                      <div class="advantage-row">
                        <!-- Первая картинка слева -->
                        <div class="advantage-icon-left">
                          <q-img
                            src="~assets/Vector 1.svg"
                            class="advantage-icon"
                            fit="contain"
                            :no-native-menu="true"
                          />
                        </div>

                        <!-- Текст по центру -->
                        <div class="advantage-text">
                          <div class="advantage-description">
                            демонстрация опыта школы к выбору будущей профессии
                          </div>
                        </div>

                        <!-- Вторая картинка справа -->
                        <div class="advantage-icon-right">
                          <q-img
                            src="~assets/Vector 2.svg"
                            class="advantage-icon"
                            fit="contain"
                            :no-native-menu="true"
                          />
                        </div>
                      </div>
                    </div>
                  </div>

                  <!-- Вторая колонка: две картинки в строку -->
                  <div class="col-12 col-md-6">
                    <div class="row q-col-gutter-md">
                      <div class="col-6">
                        <div class="advantage-image-small">
                          <q-img
                            src="~assets/Frame 2131330350.svg"
                            class="advantage-img-small"
                            fit="contain"
                            :no-native-menu="true"
                          />
                        </div>
                      </div>
                      <div class="col-6">
                        <div class="advantage-image-small">
                          <q-img
                            src="~assets/Frame 2131330349.svg"
                            class="advantage-img-small"
                            fit="contain"
                            :no-native-menu="true"
                          />
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </q-card-section>
      </q-card>
    </div>

    <!-- Секция "Виды деятельности" -->
    <div id="activities" class="activities-section">
      <div class="activities-title">Виды деятельности</div>

      <div class="activities-slider">
        <div class="activities-oval">
          <!-- Переключатель 1 -->
          <div
            class="activity-switch"
            :class="{ active: activeActivity === 'study' }"
            @click="activeActivity = 'study'"
          >
            <q-img src="~assets/activity-1.svg" class="activity-icon" fit="contain" />
            <span class="activity-text">Учебная деятельность</span>
          </div>

          <!-- Переключатель 2 -->
          <div
            class="activity-switch"
            :class="{ active: activeActivity === 'extracurricular' }"
            @click="activeActivity = 'extracurricular'"
          >
            <q-img src="~assets/activity-2.svg" class="activity-icon" fit="contain" />
            <span class="activity-text">Внеурочная деятельность</span>
          </div>

          <!-- Переключатель 3 -->
          <div
            class="activity-switch"
            :class="{ active: activeActivity === 'additional' }"
            @click="activeActivity = 'additional'"
          >
            <q-img src="~assets/activity-3.svg" class="activity-icon" fit="contain" />
            <span class="activity-text">Дополнительная деятельность</span>
          </div>
        </div>
      </div>

      <!-- Контент, который меняется при переключении -->
      <div class="activities-content">
        <!-- Учебная деятельность -->
        <div v-if="activeActivity === 'study'" class="activity-content">
          <div class="cards-grid">
            <!-- Карточка 1 -->
            <div class="activity-card card-1">
              <div class="card-header">
                <q-img src="~assets/icon.svg" class="card-icon" fit="contain" />
                <div class="card-title">Инженерные классы</div>
              </div>
              <div class="card-text">
                Специализированная программа подготовки будущих инженеров. Ученики изучают основы
                робототехники, 3D-моделирования, программирования и работы с современным
                оборудованием. Специализированная программа подготовки будущих инженеров.
              </div>
              <div class="card-files">
                <div class="files-info">
                  <div class="docs-link">
                    <q-img src="~assets/SVG.svg" class="docs-icon" fit="contain" />
                    <span>Документы</span>
                  </div>
                  <span class="files-count">2 файла</span>
                </div>
                <div class="files-list">
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-pdf.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Презентация «Инженерная вертикаль»</span>
                        <span class="file-size">PDF • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-docx.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Информация о приеме в 7 класс</span>
                        <span class="file-size">DOCX • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                </div>
              </div>
            </div>

            <!-- Карточка 2 -->
            <div class="activity-card card-2">
              <div class="card-header">
                <q-img src="~assets/icon (1).svg" class="card-icon" fit="contain" />
                <div class="card-title">Строительные классы</div>
              </div>
              <div class="card-text">
                Специализированная программа подготовки будущих инженеров. Ученики изучают основы
                робототехники, 3D-моделирования, программирования и работы с современным
                оборудованием. Специализированная программа подготовки будущих инженеров.
              </div>
              <div class="card-files">
                <div class="files-info">
                  <div class="docs-link">
                    <q-img src="~assets/SVG.svg" class="docs-icon" fit="contain" />
                    <span>Документы</span>
                  </div>
                  <span class="files-count">2 файла</span>
                </div>
                <div class="files-list">
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-pdf.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Презентация «Инженерная вертикаль»</span>
                        <span class="file-size">PDF • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-docx.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Информация о приеме в 7 класс</span>
                        <span class="file-size">DOCX • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                </div>
              </div>
            </div>

            <!-- Карточка 3 -->
            <div class="activity-card card-3">
              <div class="card-header">
                <q-img src="~assets/icon (2).svg" class="card-icon" fit="contain" />
                <div class="card-title">Профильные классы</div>
              </div>
              <div class="card-text">
                Специализированная программа подготовки будущих инженеров. Ученики изучают основы
                робототехники, 3D-моделирования, программирования и работы с современным
                оборудованием. Специализированная программа подготовки будущих инженеров.
              </div>
              <div class="card-files">
                <div class="files-info">
                  <div class="docs-link">
                    <q-img src="~assets/SVG.svg" class="docs-icon" fit="contain" />
                    <span>Документы</span>
                  </div>
                  <span class="files-count">4 файла</span>
                </div>
                <div class="files-list">
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-pdf.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Презентация «Инженерная вертикаль»</span>
                        <span class="file-size">PDF • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-docx.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Информация о приеме в 7 класс</span>
                        <span class="file-size">DOCX • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-pdf.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Презентация «Инженерная вертикаль»</span>
                        <span class="file-size">PDF • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                  <div class="file-item">
                    <div class="file-info">
                      <q-img src="~assets/icon-docx.svg" class="file-icon" fit="contain" />
                      <div class="file-details">
                        <span class="file-name">Информация о приеме в 7 класс</span>
                        <span class="file-size">DOCX • 2.4 MB</span>
                      </div>
                    </div>
                    <q-img src="~assets/icon_download.svg" class="download-icon" fit="contain" />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div v-else-if="activeActivity === 'extracurricular'" class="activity-content">
          Здесь будет контент для Внеурочной деятельности
        </div>
        <div v-else-if="activeActivity === 'additional'" class="activity-content">
          Здесь будет контент для Дополнительной деятельности
        </div>
      </div>
    </div>

    <!-- Секция "Подкасты" -->
    <div id="podcasts" class="podcasts-section">
      <div class="podcasts-container">
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
              <q-img src="~assets/arrow-right.svg" class="btn-icon" fit="contain" />
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

const activeActivity = ref('study');
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
// Hero секция на всю ширину
.hero-section {
  position: relative;
  width: 100%;
  min-height: 1016px;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50%;

  :deep(.q-img__image) {
    object-fit: cover;
    object-position: center bottom;
  }
}

.hero-overlay {
  background: rgba(0, 0, 0, 0.3);
}

.hero-content {
  max-width: 1600px;
  margin: 0 auto;
  width: 100%;
}

.hero-center-img {
  width: 100%;
  max-width: 1600px;
  height: auto;
  margin: 0 auto;

  :deep(.q-img__image) {
    object-fit: contain;
  }
}

.hero-topic-wrapper {
  text-align: center;
  margin-top: 40px;
}

.hero-topic {
  color: #505468;
  font-family: 'Mulish', sans-serif;
  font-size: 90px;
  font-weight: 700;
  line-height: 1.2;
  max-width: 1100px;
  margin-bottom: 16px;
  display: inline-flex;
}

.hero-text {
  color: #505468;
  font-family: 'Mulish', sans-serif;
  font-size: 32px;
  font-weight: 400;
  max-width: 1100px;
  display: inline-flex;
  margin: 0 auto;
}

// Основной контент
.main-content-wrapper {
  margin: 0 auto;
  position: relative;
  z-index: 3;
}

.main-card {
  top: 31px;
  background: #ffffff;
  box-shadow: 0px -31px 0px #fbc6ba !important;
  border-radius: 100px 100px 0px 0px;
}

.feature-card {
  transition: all 0.3s ease;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(4px);
  border-radius: 16px !important;

  &:hover {
    transform: translateY(-4px);
    background: white;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08) !important;
  }
}

.section-padding {
  padding: 64px 24px;
  max-width: 1200px;
  margin: 0 auto;
}

// Блок "Пространство" с фоновой картинкой
.space-section {
  position: relative;
  width: 100%;
  overflow: hidden;
}

.space-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('~assets/Rectangle 240654981.svg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0.5; // прозрачность фона, можно убрать или изменить
  pointer-events: none;
}

.space-content-wrapper {
  position: relative;
  z-index: 2;
  max-width: 1600px;
  margin: 0 auto;
  padding-top: 100px;
}

.space-content {
  display: flex;
  align-items: center;
  gap: 24px;
}

.space-image {
  flex: 1;
  max-width: 400px;
}

.space-img {
  width: 100%;
  height: auto;
}

.space-text {
  flex: 2;
  text-align: left;
}

.space-title {
  font-family: 'Mulish', sans-serif;
  font-size: 80px;
  font-weight: 700;
  color: #505468;
  line-height: 96px;
  margin-bottom: 24px;
}

.space-description {
  font-family: 'Mulish', sans-serif;
  font-size: 32px;
  font-weight: 400;
  color: #505468;
  line-height: 44px;
}
// Блок с преимуществами
.advantages-section {
  padding: 60px 0 40px;
}

.advantage-card {
  text-align: left;
  width: 100%;
}

.advantage-image {
  margin-bottom: 32px;
}

.advantage-img {
  max-width: 485px;
  height: auto;
}

.advantage-description {
  font-family: 'Mulish', sans-serif;
  font-size: 32px;
  font-weight: 400;
  color: #505468;
  line-height: 44px;
  max-width: 720px;
}

.advantage-image-small {
  width: 100%;

  .advantage-img-small {
    width: 100%;
    height: auto;
  }
}

.advantage-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  margin-top: 40px;
}

.advantage-icon-left,
.advantage-icon-right {
  flex-shrink: 0;
}

.advantage-icon {
  width: 24px;
  height: 133px;
}

.advantage-text {
  flex: 1;
}

.advantage-description {
  font-family: 'Mulish', sans-serif;
  font-size: 24px;
  font-weight: 400;
  color: #505468;
  line-height: 36px;
  margin: 0;
}

// Секция "Виды деятельности"
.activities-section {
  padding: 80px 24px;
  max-width: 1600px;
  margin: 0 auto;
}

.activities-title {
  font-family: 'Mulish', sans-serif;
  font-size: 80px;
  font-weight: 700;
  color: #505468;
  text-align: center;
  margin-bottom: 60px;
}

.activities-slider {
  display: flex;
  justify-content: center;
  margin-bottom: 60px;
}

.activities-oval {
  display: flex;
  align-items: center;
  background: #fff9f6;
  border-radius: 100px;
  padding: 4px;
}

.activity-switch {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 5px 28px;
  border-radius: 60px;
  cursor: pointer;
  transition: all 0.3s ease;
  background: transparent;

  &.active {
    background: #fbe1ba;
  }
}

.activity-icon {
  width: 16px;
  height: 16px;
}

.activity-text {
  font-family: 'Mulish', sans-serif;
  font-size: 20px;
  font-weight: 400;
  color: #6f552e;
  white-space: nowrap;
}

.activities-content {
  padding: 40px 0;
}

.activity-content {
  font-family: 'Mulish', sans-serif;
  font-size: 18px;
  color: #505468;
  line-height: 1.5;
}
// Карточки для учебной деятельности
.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.activity-card {
  background: #ffffff;
  border-radius: 40px;
  padding: 24px;
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 28px rgba(0, 0, 0, 0.1);
  }
}
.card-1 {
  box-shadow:
    0px -20px 0px 0px #ddbbfb,
    0px 0px 14px 0px rgba(80, 84, 104, 0.12);
}

// Голубая тень
.card-2 {
  box-shadow:
    0px -20px 0px 0px #dce0f4,
    0px 0px 14px 0px rgba(80, 84, 104, 0.12);
}

// Зелёная тень
.card-3 {
  box-shadow:
    0px -20px 0px 0px #fbc6ba,
    0px 0px 14px 0px rgba(80, 84, 104, 0.12);
}

.card-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}

.card-icon {
  width: 40px;
  height: 40px;
  flex-shrink: 0;
}

.card-title {
  font-family: 'Mulish', sans-serif;
  font-size: 20px;
  font-weight: 700;
  color: #505468;
  line-height: 1.3;
}

.card-text {
  font-family: 'Mulish', sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #6f6f7a;
  line-height: 1.5;
  margin-bottom: 24px;
}

.card-files {
  border-top: 1px solid #e8e8e8;
  padding-top: 16px;
}

.files-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.files-count {
  font-family: 'Mulish', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #505468;
}

.docs-link {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;

  span {
    font-family: 'Mulish', sans-serif;
    font-size: 14px;
    font-weight: 500;
    color: #505468;
  }
}

.docs-icon {
  width: 18px;
  height: 18px;
}

.files-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.file-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  border-radius: 16px;
  background-color: #f9fafb;
  padding: 12px;
  gap: 12px;

  &:hover span {
    color: #f5a623;
  }
}

.file-info {
  display: flex;
  align-items: center;
  gap: 12px;
  flex: 1;
}

.file-details {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.file-icon {
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  padding: 12px;
}

.file-name {
  font-family: 'Mulish', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #131314;
  text-decoration: none;
  transition: color 0.2s ease;
}

.file-size {
  font-family: 'Mulish', sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: #505468;
}

.download-icon {
  width: 16px;
  height: 16px;
  flex-shrink: 0;
  cursor: pointer;
}

// Секция "Подкасты"
.podcasts-section {
  padding: 80px 24px 100px;
  margin: 0 auto;
  border-radius: 100px;
  background-color: #eef2fd;
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

// Адаптив для планшетов
@media (max-width: 1024px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
}

// Адаптив для мобильных
@media (max-width: 768px) {
  .cards-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .activity-card {
    padding: 20px;
  }

  .card-title {
    font-size: 18px;
  }
}
// Адаптив для планшетов
@media (max-width: 768px) {
  .activities-section {
    padding: 60px 24px;
  }

  .activities-title {
    font-size: 40px;
    margin-bottom: 40px;
  }

  .activities-oval {
    flex-direction: column;
    border-radius: 60px;
    gap: 16px;
    padding: 20px;
  }

  .activity-switch {
    width: 100%;
    justify-content: center;
  }

  .activity-text {
    font-size: 18px;
    white-space: normal;
  }
}

// Адаптив для мобильных
@media (max-width: 480px) {
  .activities-title {
    font-size: 36px;
  }

  .activity-text {
    font-size: 16px;
  }

  .activity-icon {
    width: 24px;
    height: 24px;
  }
}
// Адаптив для планшетов
@media (max-width: 768px) {
  .advantages-section {
    padding: 40px 0;
  }

  // Перестраиваем строку преимуществ
  .row.q-col-gutter-lg {
    display: flex;
    flex-direction: column;
    gap: 40px;
  }

  // Первая колонка (с текстом и иконками)
  .col-12.col-md-6:first-child {
    order: 1; // Первая колонка сверху
  }

  // Вторая колонка (с двумя картинками)
  .col-12.col-md-6:last-child {
    order: 2; // Вторая колонка снизу
    display: flex;
    flex-direction: row;
    gap: 20px;

    .row.q-col-gutter-md {
      display: flex;
      flex-direction: row;
      width: 100%;
      gap: 20px;

      .col-6 {
        flex: 1;
        width: 50%;
      }
    }
  }

  .advantage-row {
    flex-direction: column;
    text-align: center;
    gap: 20px;
  }

  .advantage-icon {
    width: 60px;
  }

  .advantage-description {
    font-size: 22px;
    line-height: 28px;
  }

  .advantage-row {
    gap: 16px;
  }
}

// Адаптив для мобильных
@media (max-width: 480px) {
  .advantage-row {
    flex-direction: column;
    text-align: center;
    gap: 20px;
  }

  .advantage-icon-left,
  .advantage-icon-right {
    width: 50px;
  }
}
// Адаптив для планшетов
@media (max-width: 768px) {
  .advantage-title {
    font-size: 32px;
    line-height: 40px;
  }

  .advantage-image {
    margin-bottom: 24px;
  }
}

// Адаптив для мобильных
@media (max-width: 480px) {
  .advantage-title {
    font-size: 28px;
    line-height: 36px;
  }

  .advantage-image {
    text-align: center;
  }

  .advantage-card {
    text-align: center;
    margin-bottom: 40px;
  }

  .advantage-description {
    max-width: 100%;
  }
}

// Адаптив для планшетов
@media (max-width: 768px) {
  .space-description {
    font-size: 22px;
    line-height: 28px;
    max-width: 100%;
  }

  .space-title {
    font-size: 32px;
  }

  .space-content-wrapper {
    padding: 60px 24px;
  }
}

// Адаптив для мобильных
@media (max-width: 480px) {
  .space-title {
    font-size: 28px;
  }

  .space-description {
    font-size: 16px;
  }

  .space-image {
    min-width: 250px;
  }
}

// Адаптив для мобильных
@media (max-width: 1024px) {
  .hero-topic {
    font-size: 60px;
  }

  .hero-text {
    font-size: 24px;
  }

  .hero-section {
    min-height: 800px;
  }

  .space-title {
    font-size: 40px;
    line-height: 44px;
  }
}

@media (max-width: 768px) {
  .hero-section {
    min-height: 600px;
  }

  .hero-topic {
    font-size: 36px;
  }

  .hero-text {
    font-size: 18px;
    width: 80%;
  }

  .main-content-wrapper {
    margin-top: -20px;
  }
}

@media (max-width: 599px) {
  .hero-section {
    min-height: 500px;
  }

  .hero-topic {
    font-size: 28px;
  }

  .hero-text {
    font-size: 16px;
  }
}
</style>
