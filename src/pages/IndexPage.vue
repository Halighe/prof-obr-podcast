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
              демонстрация возможностей школы, систематизация и представление информации
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
                  <q-img
                    src="~assets/Frame 2131330347.svg"
                    class="space-img"
                    fit="contain"
                    :no-native-menu="true"
                  />
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

          <!-- Карточки с преимуществами -->
        </q-card-section>

        <q-card-section class="text-center q-pb-xl">
          <q-btn
            unelevated
            color="primary"
            label="Узнать больше"
            class="q-mt-lg"
            size="lg"
            no-caps
            @click="onLearnMore"
          />
        </q-card-section>
      </q-card>
    </div>

    <!-- Секция "Виды деятельности" -->
    <div id="activities" class="section-padding">
      <!-- ваш контент про виды деятельности -->
    </div>

    <!-- Секция "Подкасты" -->
    <div id="podcasts" class="section-padding">
      <!-- ваш контент про подкасты -->
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { useQuasar } from 'quasar';

const $q = useQuasar();

const onLearnMore = () => {
  $q.notify({
    message: 'Здесь будет дополнительная информация',
    color: 'primary',
    position: 'top',
    icon: 'info',
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

// Адаптив для планшетов
@media (max-width: 768px) {
  .advantages-section {
    padding: 40px 0;
  }

  .advantage-title {
    font-size: 32px;
    line-height: 40px;
  }

  .advantage-description {
    font-size: 16px;
    line-height: 24px;
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
  .space-content {
    flex-direction: column;
    text-align: center;
    gap: 40px;
  }

  .space-text {
    text-align: center;
  }

  .space-description {
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
    max-width: 250px;
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
    height: 800px;
  }
}

@media (max-width: 768px) {
  .hero-section {
    height: 600px;
  }

  .hero-topic {
    font-size: 36px;
  }

  .hero-text {
    font-size: 18px;
  }

  .main-content-wrapper {
    margin-top: -20px;
  }
}

@media (max-width: 599px) {
  .hero-section {
    height: 500px;
  }

  .hero-topic {
    font-size: 28px;
  }

  .hero-text {
    font-size: 16px;
  }
}
</style>
