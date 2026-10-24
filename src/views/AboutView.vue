<script setup>
import { onMounted, onUnmounted } from 'vue';
import AppButton from '../components/common/AppButton.vue';

onMounted(() => {
  if (typeof document !== 'undefined') {
    document.documentElement.style.backgroundColor = '#091627';
    document.body.style.backgroundColor = '#091627';
  }
});

onUnmounted(() => {
  if (typeof document !== 'undefined') {
    document.documentElement.style.backgroundColor = '';
    document.body.style.backgroundColor = '';
  }
});
</script>

<template>
  <div class="about-view" data-name="من نحن">
    <!-- Ambient Blur Glow matching Figma section glow -->
    <div
      class="about-glow section-glow"
      data-name="Section glow"
      aria-hidden="true"
    ></div>

    <section class="about-hero">
      <div class="container about-hero__container">
        <!-- Main Statement matching Figma Frame 146 -->
        <div class="about-hero__content" data-name="Frame 146">
          <h1 class="about-hero__title" data-name="Manifesto heading">
            نربط بين <span class="highlight-red">الفكرة</span>، الهوية، والنتائج.
          </h1>
          <p class="about-hero__text" data-name="Manifesto heading">
            نؤمن أن كل مشروع يستحق أكثر من مجرد تنفيذ، بل رؤية واضحة تقوده من الفكرة حتى النجاح. نجمع لك تحت سقف واحد: تحليل السوق، تطوير الأعمال، التصميم والتسويق.
          </p>

          <div class="about-hero__action">
            <AppButton
              to="/contact"
              variant="primary"
              class="about-hero__btn"
              data-name="Button"
            >
              <span class="about-hero__btn-text" data-name="Book Now">ابدأ رحلتك معنا</span>
            </AppButton>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.highlight-red {
  color: var(--color-primary);
}

.about-view {
  background-color: #091627;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  color: #FFFFFF;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

/* Ambient Section Glow matching Figma */
.about-glow {
  position: absolute;
  pointer-events: none;
  z-index: 0;
}

.section-glow {
  top: 90px;
  left: -180px;
  width: 520px;
  height: 520px;
  border-radius: 260px;
  background-color: #1A3E6F;
  opacity: 0.3;
  filter: blur(100px);
}

.about-hero {
  position: relative;
  z-index: 1;
  padding: 0;
  width: 100%;
}

.about-hero__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

/* Frame 146 matching Figma */
.about-hero__content {
  width: 848px;
  max-width: 100%;
  margin-top: 150px;
  margin-bottom: 70px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.about-hero__title {
  font-size: 56px;
  font-weight: 800;
  line-height: 72px;
  letter-spacing: -0.5px;
  color: #FBE9ED;
  margin: 0;
}

@media (max-width: 768px) {
  .about-hero__content {
    margin-top: 120px;
    margin-bottom: 50px;
    gap: 24px;
    padding: 0 16px;
  }

  .about-hero__title {
    font-size: clamp(30px, 8.5vw, 42px);
    line-height: 1.3;
  }

  .about-hero__text {
    font-size: clamp(16px, 4.5vw, 20px) !important;
    line-height: 1.6 !important;
  }
}

/* Manifesto heading body paragraph matching Figma */
.about-hero__text {
  font-size: 28px;
  font-weight: 700;
  line-height: 42px;
  color: #E8ECF1;
  margin: 0;
  text-align: center;
}

.about-hero__action {
  display: flex;
  justify-content: center;
  margin: 0;
}

/* Button matching Figma */
.about-hero__btn {
  width: 198px !important;
  height: 56px !important;
  box-shadow: none !important;
  border-radius: 12px !important;
  display: inline-flex !important;
  align-items: center !important;
  justify-content: center !important;
  padding: 0 !important;
}

/* Book Now text matching Figma */
.about-hero__btn-text {
  font-size: 16px;
  line-height: 24px;
  color: #EBECF1 !important;
  font-weight: 700;
  white-space: nowrap;
}

/* Responsive Breakpoints */
@media (max-width: 860px) {
  .about-hero__content {
    width: 100%;
    padding: 0 16px;
    gap: 28px;
    margin-top: 80px;
  }
  .about-hero__title {
    font-size: 40px;
    line-height: 54px;
  }
  .about-hero__text {
    font-size: 20px;
    line-height: 32px;
  }
}

@media (max-width: 500px) {
  .about-hero__title {
    font-size: 32px;
    line-height: 44px;
  }
  .about-hero__text {
    font-size: 17px;
    line-height: 28px;
  }
}
</style>
