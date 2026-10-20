<script setup>
import { RouterLink } from 'vue-router';
import AppButton from '../components/common/AppButton.vue';

// 4 Feature items in floating bar
const features = [
  {
    title: 'نتعامل مع عملائنا كشركاء نجاح مش مجرد عملاء',
    icon: 'handshake',
  },
  {
    title: 'نقدم حلول إبداعية تواكب احتياجات السوق',
    icon: 'cogs',
  },
  {
    title: 'نلتزم بالجودة والمواعيد في كل مشروع',
    icon: 'shield',
  },
  {
    title: 'نعمل بخطة مدروسة لتحقيق أهداف عملائنا',
    icon: 'target',
  },
];

// 4 Steps toward the top
const steps = [
  {
    title: 'دراسة السوق والمنافسين',
    desc: 'نبدأ بفهم نشاطك وتحليل السوق والمنافسين لتحديد الفرص الحقيقية ونقاط قوتك.',
    icon: 'bar-chart',
  },
  {
    title: 'التخطيط وتطوير الأعمال',
    desc: 'نضع خطة نمو واضحة بأهداف ومراحل محددة ونختار الحلول الأنسب لطبيعة مشروعك.',
    icon: 'trending-up',
  },
  {
    title: 'التصميم والتنفيذ',
    desc: 'نصمم موقعك أو تطبيقك ونبني هويتك البصرية من جرافيك وفيديوهات تعزز من علامتك.',
    icon: 'palette',
  },
  {
    title: 'الإطلاق والانتشار',
    desc: 'نفتح صفحاتك على السوشيال ميديا وننسق الإعلانات ونتابع النتائج معك خطوة بخطوة.',
    icon: 'globe',
  },
];

// 4 Highlights (Why Us)
const differentiators = [
  {
    id: '01',
    img: '/assets/num-01.png',
    title: 'حلول مخصصة',
    desc: 'رحلة متكاملة نمشيها معك، من دراسة السوق حتى الانطلاق الفعلي وتحقيق النمو.',
    reverse: false,
  },
  {
    id: '02',
    img: '/assets/num-02.png',
    title: 'فريق متكامل',
    desc: 'تحليل السوق، وتطوير الأعمال، والتصميم، والتسويق، كلها تحت سقف واحد بدل أكثر من جهة.',
    reverse: true,
  },
  {
    id: '03',
    img: '/assets/num-03.png',
    title: 'تركيز على النتائج',
    desc: 'نربط كل خطوة بأهداف تجارية واضحة، ونتابع الأداء لنتأكد أن العمل يحقق ما اتفقنا عليه.',
    reverse: false,
  },
  {
    id: '04',
    img: '/assets/num-04.png',
    title: 'وضوح في كل خطوة',
    desc: 'تعرف دائمًا أين وصل عملك، مع متابعة مستمرة وتقارير واضحة في كل مرحلة.',
    reverse: true,
  },
];

// Contact points
const contactCards = [
  {
    icon: 'building',
    title: 'زورونا',
    subtitle: 'يسعدنا استقبالكم في مكتبنا خلال ساعات العمل',
    detail: 'شارع الملك فهد، الرياض، المملكة العربية السعودية',
  },
  {
    icon: 'phone',
    title: 'اتصلوا بنا',
    subtitle: 'فريقنا متاح من الأحد إلى الخميس خلال ساعات العمل',
    detail: '+966 50 000 0000',
    link: 'tel:+966500000000',
  },
  {
    icon: 'mail',
    title: 'راسلونا',
    subtitle: 'أرسلوا لنا وسنعاود الرد خلال يوم عمل واحد',
    detail: 'sahmqima@domain.com',
    link: 'mailto:sahmqima@domain.com',
  },
];
</script>

<template>
  <div class="home-view">
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-section__bg">
        <img src="/assets/hero-bg.jpg" alt="خلفية مدينة الرياض" class="hero-section__bg-img" />
        <div class="hero-section__overlay"></div>
      </div>

      <div class="container hero-section__container">
        <div class="hero-section__content">
          <h1 class="hero-section__title">
            <span class="hero-title-block">حيث تلتقي</span>
            <span class="hero-title-block"><span class="highlight-red">الرؤية</span> بالطموح</span>
          </h1>
          <p class="hero-section__subtitle">
            حلول استشارية واستثمارية متكاملة في قلب التحول<br />
            الاقتصادي للمملكة انسجامًا مع رؤية المملكة ٢٠٣٠.
          </p>
          <div class="hero-section__actions">
            <AppButton to="/services" variant="primary" size="lg" class="hero-btn">
              استكشف الفرص
            </AppButton>
            <AppButton to="/services" variant="outline-white" size="lg" class="hero-btn">
              خدماتنا
            </AppButton>
          </div>
        </div>
      </div>

      <!-- Floating Feature Bar -->
      <div class="hero-features">
        <div class="container">
          <div class="hero-features__bar">
            <div
              v-for="(item, index) in features"
              :key="index"
              class="hero-features__item"
            >
              <div class="hero-features__icon-wrap">
                <svg v-if="item.icon === 'target'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="10"></circle>
                  <circle cx="12" cy="12" r="6"></circle>
                  <circle cx="12" cy="12" r="2"></circle>
                </svg>
                <svg v-else-if="item.icon === 'shield'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                  <polyline points="9 12 11 14 15 10"></polyline>
                </svg>
                <svg v-else-if="item.icon === 'cogs'" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="3"></circle>
                  <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
                </svg>
                <svg v-else width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="m11 17 2 2a1 1 0 0 0 1.4 0l6.6-6.6a2 2 0 0 0 0-2.8l-2.6-2.6a2 2 0 0 0-2.8 0L13 9.6"></path>
                  <path d="m13 7-2-2a2 2 0 0 0-2.8 0L3.6 9.6a2 2 0 0 0 0 2.8l6.6 6.6a1 1 0 0 0 1.4 0l1.4-1.4"></path>
                </svg>
              </div>
              <p class="hero-features__text">{{ item.title }}</p>
              <div v-if="index < features.length - 1" class="hero-features__divider" aria-hidden="true"></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services Overview Section (Hexagons) -->
    <section class="services-overview">
      <div class="container services-overview__container">
        <div class="services-overview__header">
          <h2 class="section-title">
            <span class="highlight-red">خدمات</span> متكاملة لنجاح أعمالك
          </h2>
          <p class="section-subtitle">
            خدماتنا تغطي كل ما تحتاجه شركتك من التحليل حتى الانتشار الرقمي
          </p>
        </div>

        <div class="services-overview__visual">
          <img
            src="/assets/hexagons.png"
            alt="خدمات مؤسسة سهم القمة: تحليل السوق، تطوير الأعمال، تصميم المواقع، التسويق، إدارة السوشيال ميديا"
            class="services-overview__img"
          />
        </div>
      </div>
    </section>

    <!-- 4 Steps Section (Desktop - 5) -->
    <section class="steps-section">
      <div class="container steps-section__container">
        <!-- Right Column: Info & Action -->
        <div class="steps-section__intro">
          <h2 class="steps-section__title">
            <span class="highlight-red">أربع</span> خطوات نحو القمة
          </h2>
          <p class="steps-section__desc">
            رحلة متكاملة نمشيها معك، من دراسة السوق حتى الانطلاق الفعلي وتحقيق النمو
          </p>
          <div class="steps-section__action">
            <AppButton to="/process" variant="primary" size="lg">
              ابدأ نحو القمة
            </AppButton>
          </div>
        </div>

        <!-- Left Column: 4 Cards -->
        <div class="steps-section__cards">
          <div
            v-for="(step, idx) in steps"
            :key="idx"
            class="step-card"
          >
            <div class="step-card__icon">
              <svg v-if="idx === 0" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="20" x2="18" y2="10"></line>
                <line x1="12" y1="20" x2="12" y2="4"></line>
                <line x1="6" y1="20" x2="6" y2="14"></line>
              </svg>
              <svg v-else-if="idx === 1" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline>
                <polyline points="17 6 23 6 23 12"></polyline>
              </svg>
              <svg v-else-if="idx === 2" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="13.5" cy="6.5" r=".5" fill="currentColor"></circle>
                <circle cx="17.5" cy="10.5" r=".5" fill="currentColor"></circle>
                <circle cx="8.5" cy="7.5" r=".5" fill="currentColor"></circle>
                <circle cx="6.5" cy="12.5" r=".5" fill="currentColor"></circle>
                <path d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10c.926 0 1.648-.746 1.648-1.688 0-.437-.18-.835-.437-1.125-.29-.289-.438-.652-.438-1.125a1.64 1.64 0 0 1 1.668-1.668h1.996c3.051 0 5.555-2.503 5.555-5.554C21.965 6.012 17.461 2 12 2z"></path>
              </svg>
              <svg v-else width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10"></circle>
                <line x1="2" y1="12" x2="22" y2="12"></line>
                <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path>
              </svg>
            </div>
            <h3 class="step-card__title">{{ step.title }}</h3>
            <p class="step-card__desc">{{ step.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Us Section (Desktop - 6) -->
    <section class="differentiators-section">
      <div class="container differentiators-section__container">
        <div class="differentiators-section__header">
          <h2 class="differentiators-section__badge">ما يميّزنا عن غيرنا</h2>
          <p class="differentiators-section__title">
            لأن نجاحك يبدأ بشريك <span class="highlight-navy">يفهمك</span>، و<span class="highlight-navy">يخطط</span> معك، و<span class="highlight-navy">ينفّذ</span> بإتقان
          </p>
        </div>

        <div class="differentiators-section__list">
          <div
            v-for="item in differentiators"
            :key="item.id"
            class="diff-row"
            :class="{ 'diff-row--reverse': item.reverse }"
          >
            <!-- Content: On Right for normal row in RTL -->
            <div class="diff-row__content">
              <div class="diff-row__title-wrap">
                <h3 class="diff-row__title">{{ item.title }}</h3>
                <div class="diff-row__accent-line" aria-hidden="true"></div>
              </div>
              <p class="diff-row__desc">{{ item.desc }}</p>
            </div>

            <!-- 3D Textured Number Image: On Left for normal row in RTL -->
            <div class="diff-row__media">
              <img :src="item.img" :alt="item.id" class="diff-row__num-img" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Banner & Info Section Matching Figma -->
    <section class="home-contact-section">
      <div class="home-contact-section__hero">
        <img src="/assets/contact-banner-bg.jpg" alt="خلفية تواصل معنا" class="home-contact-section__hero-bg" />
        <div class="home-contact-section__hero-overlay"></div>
        <div class="container home-contact-section__hero-content">
          <h2 class="home-contact-section__title">تواصل معنا</h2>
          <p class="home-contact-section__subtitle">
            أخبرنا بفكرتك وسنعود إليك بخطة واضحة تناسب أهدافك، خلال 24 ساعة
          </p>
        </div>
      </div>

      <!-- 3 Contact Columns directly below banner without floating card -->
      <div class="home-contact-section__info-section">
        <div class="container">
          <div class="home-contact-section__cards">
            <div
              v-for="(card, index) in contactCards"
              :key="index"
              class="contact-box"
            >
              <div class="contact-box__icon">
                <svg v-if="card.icon === 'building'" width="36" height="36" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M3 9.5L12 3l9 6.5V20a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1V9.5z"></path>
                </svg>
                <svg v-else-if="card.icon === 'phone'" width="36" height="36" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                </svg>
                <svg v-else width="36" height="36" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <rect x="2" y="4" width="20" height="16" rx="2"></rect>
                  <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"></path>
                </svg>
              </div>
              <h3 class="contact-box__title">{{ card.title }}</h3>
              <p class="contact-box__desc">{{ card.subtitle }}</p>
              <div class="contact-box__detail-wrap">
                <a v-if="card.link" :href="card.link" class="contact-box__detail contact-box__link" dir="ltr">
                  {{ card.detail }}
                </a>
                <p v-else class="contact-box__detail">
                  {{ card.detail }}
                </p>
                <div class="contact-box__line" aria-hidden="true"></div>
              </div>
            </div>
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

.highlight-navy {
  color: #1A3E6F;
  font-weight: 800;
}

/* Hero Section */
.hero-section {
  position: relative;
  min-height: 920px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-top: 140px;
  padding-bottom: 80px;
  overflow: hidden;
}

.hero-section__bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
}

.hero-section__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.hero-section__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to left,
    rgba(9, 22, 39, 0.72) 0%,
    rgba(9, 22, 39, 0.45) 50%,
    rgba(9, 22, 39, 0.6) 100%
  );
}

.hero-section__container {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.hero-section__content {
  max-width: 680px;
  color: #FFFFFF;
  margin-top: 20px;
}

.hero-section__title {
  font-size: 54px;
  font-weight: 900;
  line-height: 1.25;
  margin-bottom: 24px;
  letter-spacing: -0.5px;
  text-align: right;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.hero-title-block {
  display: block;
}

@media (min-width: 768px) {
  .hero-section__title {
    font-size: 68px;
  }
}

.hero-section__subtitle {
  font-size: 20px;
  font-weight: 500;
  line-height: 1.7;
  color: #FFFFFF;
  margin-bottom: 36px;
  max-width: 620px;
  text-align: right;
}

@media (min-width: 768px) {
  .hero-section__subtitle {
    font-size: 22px;
  }
}

.hero-section__actions {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

.hero-btn {
  border-radius: 12px !important;
  font-weight: 700;
  padding: 14px 34px;
  font-size: 17px;
}

/* Floating Feature Bar */
.hero-features {
  position: relative;
  z-index: 10;
  margin-top: 70px;
  margin-bottom: -50px;
}

.hero-features__bar {
  background: #1F242D;
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 24px;
  padding: 24px 32px;
  display: grid;
  grid-template-columns: 1fr;
  gap: 24px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
}

@media (min-width: 640px) {
  .hero-features__bar {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .hero-features__bar {
    grid-template-columns: repeat(4, 1fr);
    padding: 24px 36px;
  }
}

.hero-features__item {
  display: flex;
  align-items: center;
  gap: 14px;
  position: relative;
}

.hero-features__icon-wrap {
  flex-shrink: 0;
  width: 44px;
  height: 44px;
  color: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-features__text {
  font-size: 15px;
  font-weight: 700;
  color: #FFFFFF;
  line-height: 1.5;
}

.hero-features__divider {
  display: none;
}

@media (min-width: 1024px) {
  .hero-features__divider {
    display: block;
    position: absolute;
    left: -12px;
    top: 15%;
    bottom: 15%;
    width: 1px;
    background: rgba(255, 255, 255, 0.15);
  }
}

/* Services Overview (Hexagons) */
.services-overview {
  padding: 130px 0 80px;
  background-color: var(--color-bg-light);
  text-align: center;
}

.services-overview__header {
  margin-bottom: 50px;
}

.section-title {
  font-size: 40px;
  font-weight: 800;
  color: var(--color-navy-dark);
  margin-bottom: 16px;
}

@media (min-width: 768px) {
  .section-title {
    font-size: 48px;
  }
}

.section-subtitle {
  font-size: 20px;
  color: var(--color-text-muted);
  font-weight: 500;
}

.services-overview__visual {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

.services-overview__img {
  max-width: 1000px;
  width: 100%;
  height: auto;
  filter: drop-shadow(0 15px 35px rgba(9, 22, 39, 0.08));
  transition: transform var(--transition-normal);
}

.services-overview__img:hover {
  transform: scale(1.01);
}

/* 4 Steps Section (Dark Blue) */
.steps-section {
  background-color: var(--color-navy-dark);
  color: #FFFFFF;
  padding: 100px 0;
  position: relative;
}

.steps-section__container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 50px;
  align-items: center;
}

@media (min-width: 1024px) {
  .steps-section__container {
    grid-template-columns: 1fr 2.5fr;
  }
}

.steps-section__intro {
  display: flex;
  flex-direction: column;
  gap: 20px;
  text-align: right;
}

.steps-section__title {
  font-size: 44px;
  font-weight: 800;
  line-height: 1.3;
}

.steps-section__desc {
  font-size: 18px;
  color: var(--color-text-light);
  line-height: 1.7;
}

.steps-section__action {
  margin-top: 10px;
}

.steps-section__cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
}

@media (min-width: 640px) {
  .steps-section__cards {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1100px) {
  .steps-section__cards {
    grid-template-columns: repeat(4, 1fr);
  }
}

.step-card {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-lg);
  padding: 32px 24px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  text-align: right;
  transition: all var(--transition-normal);
}

.step-card:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(214, 33, 78, 0.4);
  transform: translateY(-6px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.25);
}

.step-card__icon {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  background: rgba(214, 33, 78, 0.15);
  color: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
}

.step-card__title {
  font-size: 19px;
  font-weight: 700;
  color: #FFFFFF;
}

.step-card__desc {
  font-size: 14px;
  line-height: 1.7;
  color: var(--color-text-light);
}

/* Differentiators (Why Us) Matching Figma Image 2 */
.differentiators-section {
  padding: 120px 0;
  background-color: #FAF7F2;
}

.differentiators-section__header {
  text-align: center;
  max-width: 760px;
  margin: 0 auto 60px;
}

.differentiators-section__badge {
  display: block;
  font-size: 30px;
  font-weight: 800;
  color: var(--color-primary);
  margin-bottom: 12px;
}

.differentiators-section__title {
  font-size: 22px;
  font-weight: 700;
  color: #2D3748;
  line-height: 1.6;
}

.differentiators-section__list {
  display: flex;
  flex-direction: column;
  max-width: 960px;
  margin: 0 auto;
}

.diff-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 50px;
  padding: 45px 0;
  border-bottom: 1px solid #E6E1D8;
}

.diff-row:last-child {
  border-bottom: none;
}

.diff-row--reverse {
  flex-direction: row-reverse;
}

@media (max-width: 768px) {
  .diff-row,
  .diff-row--reverse {
    flex-direction: column;
    text-align: center;
    gap: 30px;
  }
}

.diff-row__media {
  flex-shrink: 0;
  width: 280px;
  display: flex;
  justify-content: center;
}

.diff-row__num-img {
  width: 260px;
  height: auto;
  object-fit: contain;
  filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.08));
}

.diff-row__content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.diff-row__title-wrap {
  display: inline-flex;
  flex-direction: column;
  align-items: flex-start;
}

@media (max-width: 768px) {
  .diff-row__title-wrap {
    align-items: center;
  }
}

.diff-row__title {
  font-size: 26px;
  font-weight: 800;
  color: #1A3E6F;
}

.diff-row__accent-line {
  width: 48px;
  height: 3px;
  background-color: var(--color-primary);
  border-radius: 2px;
  margin-top: 6px;
}

.diff-row__desc {
  font-size: 16px;
  font-weight: 500;
  color: #4A5568;
  line-height: 1.8;
  max-width: 440px;
}

/* Home Contact Section Matching Figma */
.home-contact-section {
  position: relative;
  background-color: #FFFFFF;
}

.home-contact-section__hero {
  position: relative;
  min-height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
}

.home-contact-section__hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.home-contact-section__hero-overlay {
  position: absolute;
  inset: 0;
  background: rgba(9, 22, 39, 0.62);
}

.home-contact-section__hero-content {
  position: relative;
  z-index: 1;
  color: #FFFFFF;
  padding: 60px 20px;
}

.home-contact-section__title {
  font-size: 54px;
  font-weight: 900;
  color: var(--color-primary);
  margin-bottom: 16px;
}

.home-contact-section__subtitle {
  font-size: 22px;
  font-weight: 700;
  color: #FFFFFF;
}

/* 3 Contact Columns directly below banner without floating card */
.home-contact-section__info-section {
  background-color: #FFFFFF;
  padding: 70px 0 80px;
}

.home-contact-section__cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 32px;
}

@media (min-width: 768px) {
  .home-contact-section__cards {
    grid-template-columns: repeat(3, 1fr);
    gap: 0;
  }
}

.contact-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 10px;
  padding: 10px 28px;
}

@media (min-width: 768px) {
  .contact-box {
    border-left: 1px solid #E8ECF1;
  }
  .contact-box:first-child {
    border-left: none;
  }
}

@media (max-width: 767px) {
  .contact-box {
    border-bottom: 1px solid #E8ECF1;
    padding-bottom: 30px;
  }
  .contact-box:last-child {
    border-bottom: none;
  }
}

.contact-box__icon {
  color: var(--color-primary);
  margin-bottom: 4px;
}

.contact-box__title {
  font-size: 22px;
  font-weight: 800;
  color: #091627;
}

.contact-box__desc {
  font-size: 15px;
  color: #6D6F73;
  line-height: 1.6;
  min-height: 44px;
}

.contact-box__detail-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  margin-top: 6px;
}

.contact-box__detail {
  font-size: 16px;
  font-weight: 700;
  color: var(--color-primary);
}

.contact-box__link {
  transition: opacity var(--transition-fast);
}

.contact-box__link:hover {
  opacity: 0.8;
}

.contact-box__line {
  width: 40px;
  height: 2px;
  background-color: var(--color-primary);
  border-radius: 2px;
}
</style>
