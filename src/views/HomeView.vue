<script setup>
import { RouterLink } from 'vue-router';
import AppButton from '../components/common/AppButton.vue';

// 4 Feature items in floating bar matching Figma Frame 54
const features = [
  {
    title: 'نعمل بخطة مدروسة لتحقيق أهداف عملائنا',
    icon: 'target',
  },
  {
    title: 'نلتزم بالجودة والمواعيد في كل مشروع',
    icon: 'shield',
  },
  {
    title: 'نقدم حلول إبداعية تواكب احتياجات السوق',
    icon: 'cogs',
  },
  {
    title: 'نتعامل مع عملائنا كشركاء نجاح مش مجرد عملاء',
    icon: 'handshake',
  },
];

// 4 Steps toward the top matching Figma
const steps = [
  {
    title: 'دراسة السوق والمنافسين',
    desc: 'نبدأ بفهم نشاطك وتحليل السوق والمنافسين، لنحدد الفرص الحقيقية ونقاط قوتك.',
    icon: 'bar-chart',
  },
  {
    title: 'التخطيط وتطوير الأعمال',
    desc: 'نضع خطة نمو واضحة بأهداف ومراحل محددة، ونختار الحلول الأنسب لطبيعة مشروعك.',
    icon: 'trending-up',
  },
  {
    title: 'التصميم والتنفيذ',
    desc: 'نصمم موقعك أو تطبيقك ونبني هويتك البصرية، من جرافيك وفيديوهات تعبّر عن علامتك.',
    icon: 'palette',
  },
  {
    title: 'الإطلاق والانتشار',
    desc: 'نفتح صفحاتك على السوشيال ميديا وننسق الرعايات، ونتابع النتائج معك خطوة بخطوة.',
    icon: 'globe',
  },
];

// 4 Highlights (Why Us) matching Figma Desktop - 6
const differentiators = [
  {
    id: '01',
    ellipseId: '24',
    img: `${import.meta.env.BASE_URL}assets/num-01.png`,
    title: 'حلول مخصصة',
    desc: 'رحلة متكاملة نمشيها معك، من دراسة السوق حتى الانطلاق الفعلي وتحقيق النمو',
    reverse: false,
  },
  {
    id: '02',
    ellipseId: '25',
    img: `${import.meta.env.BASE_URL}assets/num-02.png`,
    title: 'فريق متكامل',
    desc: 'تحليل السوق، وتطوير الأعمال، والتصميم، والتسويق، كلها تحت سقف واحد بدل أكثر من جهة.',
    reverse: true,
  },
  {
    id: '03',
    ellipseId: '26',
    img: `${import.meta.env.BASE_URL}assets/num-03.png`,
    title: 'تركيز على النتائج',
    desc: 'نربط كل خطوة بأهداف تجارية واضحة، ونتابع الأداء لنتأكد أن العمل يحقق ما اتفقنا عليه.',
    reverse: false,
  },
  {
    id: '04',
    ellipseId: '27',
    img: `${import.meta.env.BASE_URL}assets/num-04.png`,
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
    detail: '+44 (0) 20 116-7711',
    link: 'tel:+44201167711',
  },
  {
    icon: 'mail',
    title: 'راسلونا',
    subtitle: 'أرسلوا لنا وسنعاود الرد خلال يوم عمل واحد',
    detail: 'sahmqima@domain.com',
    link: 'mailto:sahmqima@domain.com',
  },
];

// 5 Interactive Service Hexagons
const serviceHexagonsTop = [
  {
    id: 'market-analysis',
    fullTitle: 'تحليل السوق والمنافسين',
    lines: ['تحليل السوق', 'والمنافسين'],
    img: `${import.meta.env.BASE_URL}assets/تحليل السوق والمنافسين.png`,
    link: '/services#market-analysis',
    floatDelay: '0s',
  },
  {
    id: 'business-dev',
    fullTitle: 'تطوير الأعمال',
    lines: ['تطوير الأعمال'],
    img: `${import.meta.env.BASE_URL}assets/تطوير الأعمال.png`,
    link: '/services#business-dev',
    floatDelay: '-2.2s',
  },
  {
    id: 'web-apps',
    fullTitle: 'تصميم وبرمجة المواقع والتطبيقات',
    lines: ['تصميم وبرمجة', 'المواقع والتطبيقات'],
    img: `${import.meta.env.BASE_URL}assets/تصميم وبرمجة المواقع والتطبيقات.png`,
    link: '/services#web-apps',
    floatDelay: '-4.4s',
  },
];

const serviceHexagonsBottom = [
  {
    id: 'marketing',
    fullTitle: 'التسويق',
    lines: ['التسويق'],
    img: `${import.meta.env.BASE_URL}assets/التسويق بالفيديو والجرافيك ديزاين.png`,
    link: '/services#marketing',
    floatDelay: '-1.2s',
  },
  {
    id: 'social-media',
    fullTitle: 'إدارة منصات التواصل الإجتماعي',
    lines: ['إدارة منصات التواصل', 'الإجتماعي'],
    img: `${import.meta.env.BASE_URL}assets/إدارة السوشيال ميديا.png`,
    link: '/services#social-media',
    floatDelay: '-3.4s',
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
            حلول استشارية واستثمارية متكاملة في قلب التحول الاقتصادي للمملكة انسجامًا مع رؤية المملكة ٢٠٣٠.
          </p>
          <div class="hero-section__actions">
            <RouterLink to="/services" custom v-slot="{ navigate }">
              <button @click="navigate" class="hero-btn hero-btn--primary">
                استكشف الفرص
              </button>
            </RouterLink>
            <RouterLink to="/services" custom v-slot="{ navigate }">
              <button @click="navigate" class="hero-btn hero-btn--outline">
                خدماتنا
              </button>
            </RouterLink>
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
                <svg v-if="item.icon === 'target'" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="10"></circle>
                  <circle cx="12" cy="12" r="6"></circle>
                  <circle cx="12" cy="12" r="2"></circle>
                </svg>
                <svg v-else-if="item.icon === 'shield'" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                  <polyline points="9 12 11 14 15 10"></polyline>
                </svg>
                <svg v-else-if="item.icon === 'cogs'" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="3"></circle>
                  <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
                </svg>
                <svg v-else width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
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
            خدماتنا تغطي كل ما تحتاجه شركتك من التحليل حتى الانتشار الرقمي.
          </p>
        </div>

        <div class="services-overview__visual" aria-label="خدمات سهم القمة المتكاملة">
          <div class="services-hex-cluster">
            <!-- Top Row (3 Hexagons in RTL: Market Analysis -> Business Dev -> Web & Apps) -->
            <div class="services-hex-row services-hex-row--top">
              <div
                v-for="hex in serviceHexagonsTop"
                :key="hex.id"
                class="services-hex-wrapper"
                :style="{ animationDelay: hex.floatDelay }"
              >
                <RouterLink
                  :to="hex.link"
                  class="services-hex-card"
                  :aria-label="hex.fullTitle"
                >
                  <img
                    :src="hex.img"
                    :alt="hex.fullTitle"
                    class="services-hex-card__img"
                    loading="lazy"
                  />
                  <div class="services-hex-card__overlay" aria-hidden="true">
                    <span class="services-hex-card__text">
                      <span
                        v-for="(line, lineIdx) in hex.lines"
                        :key="lineIdx"
                        class="services-hex-card__text-line"
                      >
                        {{ line }}
                      </span>
                    </span>
                  </div>
                </RouterLink>
              </div>
            </div>

            <!-- Bottom Row (2 Hexagons in RTL: Marketing -> Social Media) -->
            <div class="services-hex-row services-hex-row--bottom">
              <div
                v-for="hex in serviceHexagonsBottom"
                :key="hex.id"
                class="services-hex-wrapper"
                :style="{ animationDelay: hex.floatDelay }"
              >
                <RouterLink
                  :to="hex.link"
                  class="services-hex-card"
                  :aria-label="hex.fullTitle"
                >
                  <img
                    :src="hex.img"
                    :alt="hex.fullTitle"
                    class="services-hex-card__img"
                    loading="lazy"
                  />
                  <div class="services-hex-card__overlay" aria-hidden="true">
                    <span class="services-hex-card__text">
                      <span
                        v-for="(line, lineIdx) in hex.lines"
                        :key="lineIdx"
                        class="services-hex-card__text-line"
                      >
                        {{ line }}
                      </span>
                    </span>
                  </div>
                </RouterLink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 4 Steps Section (Desktop - 5) -->
    <section class="steps-section">
      <div class="container steps-section__container">
        <!-- Right Column: Info & Action -->
        <div class="steps-section__intro">
          <h2 class="steps-section__title">
            <span class="steps-title-line"><span class="highlight-red">أربع</span> خطوات</span>
            <span class="steps-title-line">نحو القمة</span>
          </h2>
          <p class="steps-section__desc">
            رحلة متكاملة نمشيها معك، من دراسة السوق حتى الانطلاق الفعلي وتحقيق النمو
          </p>
          <div class="steps-section__action">
            <RouterLink to="/process" custom v-slot="{ navigate }">
              <button @click="navigate" class="steps-btn">
                ابدأ نحو القمة
              </button>
            </RouterLink>
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
              <svg v-if="idx === 0" width="35" height="35" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="18" y1="20" x2="18" y2="10"></line>
                <line x1="12" y1="20" x2="12" y2="4"></line>
                <line x1="6" y1="20" x2="6" y2="14"></line>
              </svg>
              <svg v-else-if="idx === 1" width="35" height="35" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline>
                <polyline points="17 6 23 6 23 12"></polyline>
              </svg>
              <svg v-else-if="idx === 2" width="35" height="35" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="13.5" cy="6.5" r=".5" fill="currentColor"></circle>
                <circle cx="17.5" cy="10.5" r=".5" fill="currentColor"></circle>
                <circle cx="8.5" cy="7.5" r=".5" fill="currentColor"></circle>
                <circle cx="6.5" cy="12.5" r=".5" fill="currentColor"></circle>
                <path d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10c.926 0 1.648-.746 1.648-1.688 0-.437-.18-.835-.437-1.125-.29-.289-.438-.652-.438-1.125a1.64 1.64 0 0 1 1.668-1.668h1.996c3.051 0 5.555-2.503 5.555-5.554C21.965 6.012 17.461 2 12 2z"></path>
              </svg>
              <svg v-else width="35" height="35" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
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
          <h2 class="differentiators-section__main-title">ما يميّزنا عن غيرنا</h2>
          <p class="differentiators-section__title">
            لأن نجاحك يبدأ بشريك <span class="highlight-navy">يفهمك</span>، ويخطط معك، <span class="highlight-navy">وينفذ</span> بإتقان
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
              <div class="diff-row__ellipse" :class="`ellipse-${item.ellipseId}`" aria-hidden="true"></div>
              <img :src="item.img" :alt="item.id" class="diff-row__num-img" />
              <span class="diff-row__num-label">{{ item.id }}</span>
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
  min-height: 860px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 170px;
  padding-bottom: 0;
  z-index: 2;
}

@media (max-width: 768px) {
  .hero-section {
    min-height: auto;
    padding-top: 110px;
    padding-bottom: 40px;
  }
}

.hero-section__bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  overflow: hidden;
}

.hero-section__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  animation: hero-background-drift 18s ease-in-out infinite alternate;
  transform-origin: center;
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
  flex: 1;
  padding-bottom: 24px;
}

.hero-section__content {
  width: 100%;
  max-width: 636px;
  color: #FFFFFF;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.hero-section__title {
  font-family: var(--font-cairo);
  font-size: 72px;
  font-weight: 900;
  line-height: 82.8px;
  margin-bottom: 24px;
  letter-spacing: -0.5px;
  text-align: right;
  display: flex;
  flex-direction: column;
}

@media (max-width: 768px) {
  .hero-section__content {
    gap: 24px;
  }

  .hero-section__title {
    font-size: 44px;
    line-height: 52px;
    margin-bottom: 18px;
  }
}

.hero-title-block {
  display: block;
}

.hero-section__subtitle {
  font-size: 28px;
  font-weight: 700;
  line-height: 42px;
  color: #EDEDED;
  margin-bottom: 0;
  max-width: 636px;
  text-align: right;
}

@media (max-width: 768px) {
  .hero-section__subtitle {
    font-size: 18px;
    line-height: 28px;
  }
}

.hero-section__actions {
  display: flex;
  align-items: center;
  gap: 24px;
  flex-wrap: wrap;
}

.hero-btn {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  box-shadow: none !important;
  cursor: pointer;
  transition: all var(--transition-normal);
}

.hero-btn--primary {
  padding: 14px 34px;
  background: var(--color-primary);
  color: #FFFFFF;
  border: none;
  border-radius: 12px;
}

.hero-btn--primary:hover {
  background: var(--color-primary-hover);
  transform: translateY(-2px);
}

.hero-btn--outline {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 14px 34px !important;
  border: 1.5px solid rgba(255, 255, 255, 0.75) !important;
  border-radius: 12px !important;
  background: rgba(9, 22, 39, 0.45) !important;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  color: #FFFFFF !important;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  transition: all var(--transition-normal);
}

.hero-btn--outline:hover {
  background: rgba(255, 255, 255, 0.2) !important;
  border-color: #FFFFFF !important;
  transform: translateY(-2px);
}

/* Floating Feature Bar on the boundary between Hero and Services */
.hero-features {
  position: relative;
  z-index: 20;
  width: 100%;
  margin-top: auto;
  margin-bottom: 0;
}

@media (min-width: 1024px) {
  .hero-features {
    transform: translateY(50%);
  }
}

.hero-features__bar {
  background: rgba(14, 20, 27, 0.88);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 28px;
  padding: 0;
  display: grid;
  grid-template-columns: 1fr;
  box-shadow: none;
  width: 100%;
  max-width: 1248px;
  margin: 0 auto;
}

@media (min-width: 640px) {
  .hero-features__bar {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .hero-features__bar {
    grid-template-columns: repeat(4, 1fr);
    height: 145px;
  }
}

.hero-features__item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 12px;
  position: relative;
  width: 100%;
  height: 100%;
  padding: 16px 20px;
}

@media (min-width: 1024px) {
  .hero-features__item {
    padding: 0 20px;
  }
}

.hero-features__icon-wrap {
  flex-shrink: 0;
  width: 36px;
  height: 36px;
  color: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-features__text {
  font-size: 16px;
  font-weight: 500;
  color: #FFFFFF;
  line-height: 24px;
  text-align: center;
  margin: 0;
}

.hero-features__divider {
  display: none;
}

@media (min-width: 1024px) {
  .hero-features__divider {
    display: block;
    position: absolute;
    left: 0;
    top: 6px;
    bottom: 6px;
    width: 1px;
    background: rgba(255, 255, 255, 0.15);
  }
}

/* Services Overview (Hexagons - Desktop - 4) */
.services-overview {
  padding: 130px 0 80px;
  background-color: #F5F0EC;
  text-align: center;
  position: relative;
  z-index: 1;
}

@media (max-width: 768px) {
  .services-overview {
    padding-top: 60px;
    padding-bottom: 60px;
  }
}

.services-overview__header {
  margin: 0 auto 39px;
  max-width: 540px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.section-title {
  font-size: 48px;
  font-weight: 800;
  color: #153259;
  line-height: 60px;
  margin-bottom: 0;
}

.section-subtitle {
  font-size: 14px;
  color: #4A4A4A;
  font-weight: 500;
  line-height: 20px;
}

.services-overview__visual {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  position: relative;
}

/* Honeycomb Hexagon Cluster Layout */
.services-hex-cluster {
  --hex-w: 254px;
  --hex-h: calc(var(--hex-w) * 310 / 267);
  --hex-gap: calc(var(--hex-w) * 0.055);
  --hex-overlap: calc(var(--hex-h) * 0.25);
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 904.3px;
  margin: 0 auto;
  position: relative;
  padding: 0;
}

.services-hex-row {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: var(--hex-gap);
  width: 100%;
}

.services-hex-row--top {
  position: relative;
  z-index: 1;
}

.services-hex-row--bottom {
  position: relative;
  margin-top: calc(-1 * var(--hex-overlap));
  z-index: 2;
}

/* Individual Hexagon Wrapper & Float Animation */
.services-hex-wrapper {
  flex: 0 0 var(--hex-w);
  width: var(--hex-w);
  height: var(--hex-h);
  animation: hex-float 6.5s ease-in-out infinite;
  will-change: transform;
  position: relative;
}

.services-hex-wrapper:hover,
.services-hex-wrapper:focus-within {
  animation-play-state: paused;
  z-index: 10;
}

/* Hexagon Card Link */
.services-hex-card {
  position: relative;
  display: block;
  width: 100%;
  height: 100%;
  text-decoration: none;
  cursor: pointer;
  border-radius: 0;
  outline: none;
  filter: drop-shadow(0 14px 28px rgba(9, 22, 39, 0.1));
  transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.35s ease;
}

.services-hex-card:hover,
.services-hex-card:focus-visible {
  transform: translateY(-8px) scale(1.05);
  filter: drop-shadow(0 22px 42px rgba(9, 22, 39, 0.25));
  z-index: 15;
}

.services-hex-card:focus-visible {
  outline: 2px solid var(--color-red-primary);
  outline-offset: 4px;
}

/* Hexagon Image */
.services-hex-card__img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  transition: filter 0.35s ease, transform 0.35s ease;
}

.services-hex-card:hover .services-hex-card__img,
.services-hex-card:focus-visible .services-hex-card__img {
  filter: brightness(0.85) contrast(1.02);
}

/* Overlay Mask Matching Figma Design */
.services-hex-card__overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  text-align: center;
  clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
  background: linear-gradient(180deg, rgba(16, 32, 56, 0.4) 0%, rgba(10, 22, 40, 0.65) 100%);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.services-hex-card:hover .services-hex-card__overlay,
.services-hex-card:focus-visible .services-hex-card__overlay {
  opacity: 1;
}

/* Arabic Text Reveal Inside Hexagon */
.services-hex-card__text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 4px;
  color: #FFFFFF;
  font-family: var(--font-family);
  font-weight: 700;
  font-size: clamp(14px, 2vw, 20px);
  line-height: 1.45;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.6);
  transform: translateY(6px);
  transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
  user-select: none;
}

.services-hex-card:hover .services-hex-card__text,
.services-hex-card:focus-visible .services-hex-card__text {
  transform: translateY(0);
}

.services-hex-card__text-line {
  display: block;
  white-space: nowrap;
}

/* Organic Floating Animation */
@keyframes hex-float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}

/* Responsive Scaling for Honeycomb Cluster */
@media (min-width: 1200px) {
  .services-hex-cluster {
    --hex-w: 260px;
  }
}

@media (max-width: 991px) {
  .services-hex-cluster {
    --hex-w: 210px;
  }
}

@media (max-width: 767px) {
  .services-hex-cluster {
    --hex-w: clamp(96px, 28vw, 150px);
  }

  .services-hex-card__text {
    font-size: clamp(10px, 2.5vw, 13px);
    line-height: 1.35;
  }
}

/* 4 Steps Section (Desktop - 5) */
.steps-section {
  background-color: #17202B;
  color: #FFFFFF;
  padding: 100px 0;
  position: relative;
}

.steps-section__container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 89px;
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
  gap: 28px;
  text-align: right;
  align-items: flex-start;
}

.steps-section__title {
  font-size: 48px;
  font-weight: 800;
  line-height: 60px;
  color: #FFFFFF;
  margin: 0;
  text-align: right;
}

.steps-title-line {
  display: block;
}

.steps-section__desc {
  font-size: 20px;
  font-weight: 700;
  color: #EBEBEB;
  line-height: 34px;
  text-align: right;
  max-width: 380px;
  margin: 0;
}

.steps-section__action {
  margin-top: 10px;
  text-align: right;
}

.steps-btn {
  background-color: #D6214E !important;
  border-radius: 10px !important;
  border: none !important;
  box-shadow: none !important;
  padding: 14px 34px;
  font-weight: 700;
  font-size: 16px;
  color: #FFFFFF !important;
  cursor: pointer;
  display: inline-block;
  transition: all var(--transition-normal);
}

.steps-btn:hover {
  background-color: var(--color-primary-hover) !important;
  transform: translateY(-2px);
}

@media (max-width: 768px) {
  .steps-section {
    padding: 60px 0;
  }

  .steps-section__container {
    gap: 40px;
  }

  .steps-section__intro {
    align-items: flex-start;
    text-align: right;
    gap: 20px;
  }

  .steps-section__title {
    font-size: 38px;
    line-height: 48px;
    text-align: right;
  }

  .steps-section__desc {
    font-size: 17px;
    line-height: 28px;
    text-align: right;
    max-width: 100%;
  }

  .steps-section__action {
    text-align: right;
    width: 100%;
  }

  .steps-btn {
    width: auto;
  }
}

.steps-section__cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 40px;
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
  background: rgba(28, 28, 28, 0.15);
  border: none;
  border-radius: 12px;
  height: 270px;
  padding: 24px 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 16px;
  text-align: center;
  transition: all var(--transition-normal);
}

.step-card:hover {
  background: rgba(28, 28, 28, 0.3);
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
  font-size: 16px;
  font-weight: 700;
  line-height: 24px;
  color: #FFFFFF;
  text-align: center;
}

.step-card__desc {
  font-size: 12px;
  font-weight: 500;
  line-height: 18px;
  color: #FFFFFF;
  text-align: center;
}

/* Differentiators (Why Us - Desktop - 6) */
.differentiators-section {
  padding: 130px 0;
  background-color: #FAF7F2;
  min-height: 2004px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.differentiators-section__container {
  max-width: 921px;
  padding: 0;
}

.differentiators-section__header {
  text-align: center;
  max-width: 580px;
  margin: 0 auto 50px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.differentiators-section__main-title {
  font-size: 48px;
  font-weight: 800;
  line-height: 60px;
  color: var(--color-primary);
  margin: 0;
  border: none;
  padding: 0;
}

.differentiators-section__title {
  font-size: 26px;
  font-weight: 700;
  color: #696969;
  line-height: 42px;
  margin: 0;
}

.differentiators-section__title .highlight-navy {
  color: #1A3E6F;
  font-weight: 800;
}

.differentiators-section__list {
  display: flex;
  flex-direction: column;
  max-width: 921px;
  margin: 0 auto;
  gap: 0;
}

.diff-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
  padding: 65px 0;
  border-bottom: 1px solid #E6E1D8;
}

.diff-row:last-child {
  border-bottom: none;
}

.diff-row--reverse {
  flex-direction: row-reverse;
}

@media (max-width: 768px) {
  .differentiators-section__header {
    margin-bottom: 36px;
    gap: 12px;
  }

  .differentiators-section__main-title {
    font-size: 32px;
    line-height: 42px;
  }

  .differentiators-section__title {
    font-size: 20px;
    line-height: 32px;
  }

  .diff-row,
  .diff-row--reverse {
    flex-direction: column;
    text-align: center;
    gap: 30px;
    padding: 40px 0;
  }

  .diff-row__media {
    width: 100%;
    max-width: 280px;
    height: auto;
  }

  .diff-row__content {
    width: 100%;
    max-width: 100%;
  }

  .differentiators-section {
    min-height: auto;
    padding: 70px 0;
  }
}

.diff-row__media {
  position: relative;
  flex-shrink: 0;
  width: 380px;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.diff-row__ellipse {
  position: absolute;
  width: 260px;
  height: 260px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(214, 33, 78, 0.08) 0%, rgba(214, 33, 78, 0) 70%);
  pointer-events: none;
}

.diff-row__num-label {
  position: absolute;
  opacity: 0;
  pointer-events: none;
  font-size: 1px;
}

.diff-row__num-img {
  width: 260px;
  height: auto;
  object-fit: contain;
  filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.08));
  animation: visual-float 6s ease-in-out infinite;
  position: relative;
  z-index: 1;
}

.diff-row:nth-child(even) .diff-row__num-img {
  animation-delay: -3s;
}

@keyframes hero-background-drift {
  from { transform: scale(1); }
  to { transform: scale(1.06); }
}

@keyframes visual-float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@media (prefers-reduced-motion: reduce) {
  .hero-section__bg-img,
  .services-hex-wrapper,
  .diff-row__num-img {
    animation: none;
  }
}

.diff-row__content {
  width: 400px;
  max-width: 400px;
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
  font-size: 32px;
  font-weight: 800;
  line-height: 48px;
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
  color: #4A4A4A;
  line-height: 28px;
  max-width: 400px;
}

/* Home Contact Section Matching Figma */
.home-contact-section {
  position: relative;
  background-color: #FFFFFF;
}

.home-contact-section__hero {
  position: relative;
  height: 550px;
  min-height: 550px;
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
  background: rgba(9, 22, 39, 0.28);
}

.home-contact-section__hero-content {
  position: relative;
  z-index: 1;
  color: #FFFFFF;
  padding: 0;
  max-width: 628px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.home-contact-section__title {
  font-size: 72px;
  font-weight: 800;
  line-height: 108px;
  color: var(--color-primary);
  margin-bottom: 0;
  text-shadow: 0 4px 16px rgba(0, 0, 0, 0.35);
}

.home-contact-section__subtitle {
  font-size: 22px;
  font-weight: 800;
  line-height: 33px;
  color: #FFFFFF;
  margin: 0;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.45);
}

/* 3 Contact Columns directly below banner */
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
  justify-content: center;
  text-align: center;
  gap: 10px;
  padding: 10px 28px;
  height: 302px;
}

@media (min-width: 768px) {
  .contact-box {
    border-right: 1px solid rgba(0, 0, 0, 0.2);
    border-left: none;
  }
  .contact-box:first-child {
    border-right: none;
  }
}

@media (max-width: 767px) {
  .contact-box {
    border-bottom: 1px solid #E8ECF1;
    padding-bottom: 30px;
    height: auto;
  }
  .contact-box:last-child {
    border-bottom: none;
  }
}

.contact-box__icon svg {
  width: 58px;
  height: 58px;
  color: var(--color-primary);
}

.contact-box__title {
  font-size: 27px;
  font-weight: 700;
  color: #242A32;
  line-height: 33.8px;
}

.contact-box__desc {
  font-size: 16px;
  font-weight: 500;
  color: #616161;
  line-height: 27.2px;
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
  font-size: 17px;
  font-weight: 500;
  color: var(--color-primary);
  line-height: 24.7px;
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
