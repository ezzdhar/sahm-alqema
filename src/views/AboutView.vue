<script setup>
import AppButton from '../components/common/AppButton.vue';

const pillars = [
  {
    title: 'رؤيتنا',
    desc: 'أن نكون الشريك الاستراتيجي الأكثر تأثيرًا وتميزًا في تمكين الشركات وتحقيق تطلعات رؤية المملكة ٢٠٣٠.',
    icon: 'eye',
  },
  {
    title: 'رسالتنا',
    desc: 'تقديم حلول متكاملة تدمج بين التحليل الدقيق والتصميم المبتكر والتسويق الفعّال تحت سقف واحد.',
    icon: 'compass',
  },
  {
    title: 'قيمنا',
    desc: 'الشراكة الصادقة، الالتزام بأعلى معايير الجودة، الشفافية المطلقة، والتركيز الراسخ على النتائج القابلة للقياس.',
    icon: 'award',
  },
];
</script>

<template>
  <div class="about-view">
    <!-- Ambient Blur Glows matching Figma section glow -->
    <div class="about-glow about-glow--1" aria-hidden="true"></div>
    <div class="about-glow about-glow--2" aria-hidden="true"></div>

    <section class="about-hero">
      <div class="container about-hero__container">
        <!-- Main Statement from Figma -->
        <div class="about-hero__content">
          <h1 class="about-hero__title">
            نربط بين <span class="highlight-red">الفكرة</span>، الهوية، والنتائج.
          </h1>
          <p class="about-hero__text">
            نؤمن أن كل مشروع يستحق أكثر من مجرد تنفيذ، بل رؤية واضحة تقوده من الفكرة حتى النجاح. نجمع لك تحت سقف واحد: تحليل السوق، تطوير الأعمال، التصميم والتسويق.
          </p>

          <div class="about-hero__action">
            <AppButton to="/contact" variant="primary" size="lg">
              ابدأ رحلتك معنا
            </AppButton>
          </div>
        </div>

        <!-- Strategic Pillars / Pillars Cards -->
        <!-- <div class="about-pillars">
          <div
            v-for="(pillar, index) in pillars"
            :key="index"
            class="pillar-card"
          >
            <div class="pillar-card__icon">
              <svg v-if="pillar.icon === 'eye'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M2 12s3-7 10-7 10 7 10 7-3 7-10 7-10-7-10-7Z"></path>
                <circle cx="12" cy="12" r="3"></circle>
              </svg>
              <svg v-else-if="pillar.icon === 'compass'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10"></circle>
                <polygon points="16.24 7.76 14.12 14.12 7.76 16.24 9.88 9.88 16.24 7.76"></polygon>
              </svg>
              <svg v-else width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="8" r="7"></circle>
                <polyline points="8.21 13.89 7 23 12 20 17 23 15.79 13.88"></polyline>
              </svg>
            </div>
            <h3 class="pillar-card__title">{{ pillar.title }}</h3>
            <p class="pillar-card__desc">{{ pillar.desc }}</p>
          </div>
        </div> -->
      </div>
    </section>
  </div>
</template>

<style scoped>
.highlight-red {
  color: var(--color-primary);
}

.about-view {
  background-color: var(--color-navy-dark);
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  color: #FFFFFF;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

/* Ambient Glows */
.about-glow {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  filter: blur(100px);
  z-index: 0;
}

.about-glow--1 {
  width: 520px;
  height: 520px;
  top: 10%;
  right: -100px;
  background: rgba(26, 62, 111, 0.45);
}

.about-glow--2 {
  width: 450px;
  height: 450px;
  bottom: 10%;
  left: -80px;
  background: rgba(214, 33, 78, 0.15);
}

.about-hero {
  position: relative;
  z-index: 1;
  padding: 160px 0 100px;
}

.about-hero__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.about-hero__content {
  max-width: 880px;
  margin-bottom: 70px;
}

.about-hero__title {
  font-size: 54px;
  font-weight: 800;
  line-height: 1.35;
  margin-bottom: 28px;
  letter-spacing: -0.5px;
}

@media (min-width: 768px) {
  .about-hero__title {
    font-size: 64px;
  }
}

.about-hero__text {
  font-size: 24px;
  font-weight: 500;
  line-height: 1.8;
  color: #E8ECF1;
  margin-bottom: 40px;
}

@media (max-width: 768px) {
  .about-hero__text {
    font-size: 20px;
  }
}

.about-hero__action {
  display: flex;
  justify-content: center;
}

/* Pillars */
.about-pillars {
  display: grid;
  grid-template-columns: 1fr;
  gap: 24px;
  width: 100%;
  max-width: 1100px;
}

@media (min-width: 768px) {
  .about-pillars {
    grid-template-columns: repeat(3, 1fr);
  }
}

.pillar-card {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-xl);
  padding: 36px 28px;
  text-align: right;
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  transition: all var(--transition-normal);
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.pillar-card:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(214, 33, 78, 0.4);
  transform: translateY(-6px);
  box-shadow: 0 16px 36px rgba(0, 0, 0, 0.35);
}

.pillar-card__icon {
  width: 52px;
  height: 52px;
  border-radius: var(--radius-md);
  background: rgba(214, 33, 78, 0.15);
  color: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
}

.pillar-card__title {
  font-size: 22px;
  font-weight: 700;
  color: #FFFFFF;
}

.pillar-card__desc {
  font-size: 15px;
  color: var(--color-text-light);
  line-height: 1.8;
}
</style>
