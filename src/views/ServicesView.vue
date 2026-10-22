<script setup>
import { ref } from 'vue';
import AppButton from '../components/common/AppButton.vue';

const activeFilter = ref('all');

const services = [
  {
    id: 'market-analysis',
    number: '01',
    title: 'تحليل السوق والمنافسين',
    titleColor: '#142F53',
    accentColor: '#D6214E',
    watermarkColor: 'rgba(214, 33, 78, 0.2)',
    lineColor: '#E391A6',
    dotColor: '#FF315F',
    quote: 'قبل أن تخطو خطوتك، اعرف أين تقف',
    desc: 'من دراسة حجم السوق إلى تفكيك المنافسين، نقدم لك صورة واضحة تبني عليها قراراتك بثقة، عبر بيانات حقيقية لا تخمين فيها.',
    tools: ['Google Trends', 'Google Forms', 'Power BI'],
    btnText: 'اطلب دراسة السوق',
    btnVariant: 'primary',
    deliverablesCount: '06',
    minHeight: '790px',
    deliverables: [
      { id: '01', text: 'تحليل السوق والمنافسين' },
      { id: '02', text: 'تحليل المنافسين المباشرين' },
      { id: '03', text: 'تحليل SWOT' },
      { id: '04', text: 'تحليل المنافسين غير المباشرين' },
      { id: '05', text: 'مقارنة الأسعار والعروض' },
      { id: '06', text: 'تقرير شامل بالتوصيات' },
    ],
  },
  {
    id: 'business-dev',
    number: '02',
    title: 'تطوير الأعمال',
    titleColor: '#D6214E',
    accentColor: '#1A3E6F',
    watermarkColor: 'rgba(26, 62, 111, 0.2)',
    lineColor: '#B8C3D2',
    dotColor: '#82E2D0',
    quote: 'الفكرة الجيدة تحتاج خطة أفضل',
    desc: 'نبني معك خطة نمو بأهداف ومراحل محددة، ونطوّر نموذج عملك ليكون جاهزًا للتوسع بثقة.',
    tools: ['Business Model Canvas', 'Notion', 'Google Sheets'],
    btnText: 'ناقش مشروعك',
    btnVariant: 'dark',
    deliverablesCount: '06',
    minHeight: '790px',
    deliverables: [
      { id: '01', text: 'خطط عمل متكاملة' },
      { id: '02', text: 'نماذج عمل (Business Model)' },
      { id: '03', text: 'استراتيجيات تسعير' },
      { id: '04', text: 'خطط دخول السوق' },
      { id: '05', text: 'دراسات جدوى مبدئية' },
      { id: '06', text: 'خطط توسع ونمو' },
    ],
  },
  {
    id: 'web-apps',
    number: '03',
    title: 'تصميم وبرمجة المواقع والتطبيقات',
    titleColor: '#142F53',
    accentColor: '#D6214E',
    watermarkColor: 'rgba(214, 33, 78, 0.2)',
    lineColor: '#E391A6',
    dotColor: '#EAF44A',
    quote: 'موقعك واجهة أعمالك، فلنبنِه كما تستحق',
    desc: 'نصمم ونبرمج مواقع وتطبيقات حسب احتياج مشروعك، بتجربة استخدام سلسة ودعم كامل للعربية.',
    tools: ['Figma', 'Flutter', 'Node.js', 'Next.js'],
    btnText: 'ابدأ بناء موقعك',
    btnVariant: 'primary',
    deliverablesCount: '06',
    minHeight: '847px',
    deliverables: [
      { id: '01', text: 'مواقع تعريفية للشركات' },
      { id: '02', text: 'متاجر إلكترونية' },
      { id: '03', text: 'تطبيقات موبايل' },
      { id: '04', text: 'لوحات تحكم وإدارة' },
      { id: '05', text: 'صفحات هبوط' },
      { id: '06', text: 'مواقع حجز وخدمات' },
    ],
  },
  {
    id: 'marketing',
    number: '04',
    title: 'التسويق',
    titleColor: '#D6214E',
    accentColor: '#1A3E6F',
    watermarkColor: 'rgba(26, 62, 111, 0.2)',
    lineColor: '#B8C3D2',
    dotColor: '#FFFFFF',
    quote: 'المحتوى الذي يُرى يُذكر، والذي يُذكر يُباع',
    desc: 'فيديوهات وتصميمات ورعايات تحكي قصة علامتك وتوصلها للجمهور الصحيح.',
    tools: ['Illustrator', 'Photoshop', 'CapCut'],
    btnText: 'ابدأ حملتك التسويقية',
    btnVariant: 'dark',
    deliverablesCount: '05',
    minHeight: '790px',
    deliverables: [
      { id: '01', text: 'فيديوهات دعائية' },
      { id: '02', text: 'موشن جرافيك ومونتاج' },
      { id: '03', text: 'هويات بصرية' },
      { id: '04', text: 'حملات إعلانية بصرية' },
      { id: '05', text: 'محتوى إعلاني مكتوب' },
    ],
  },
  {
    id: 'social-media',
    number: '05',
    pillTitle: 'إدارة منصات التواصل الإجتماعي',
    title: 'إدارة السوشيال ميديا',
    titleColor: '#142F53',
    accentColor: '#D6214E',
    watermarkColor: 'rgba(214, 33, 78, 0.2)',
    lineColor: '#E391A6',
    dotColor: '#FF315F',
    quote: 'حضورك الرقمي هو أول انطباع عنك',
    desc: 'نفتح صفحاتك وندير محتواها وتفاعلها، ونتابع الأداء بتقارير واضحة كل شهر.',
    tools: ['Google Analytics', 'Canva', 'Meta Business Suite', 'Next.js'],
    btnText: 'عزّز حضورك الآن',
    btnVariant: 'primary',
    deliverablesCount: '05',
    minHeight: '847px',
    deliverables: [
      { id: '01', text: 'حسابات جاهزة ومجهزة' },
      { id: '02', text: 'تقويم محتوى شهري' },
      { id: '03', text: 'تصميمات ومنشورات يومية' },
      { id: '04', text: 'إدارة التفاعل والردود' },
      { id: '05', text: 'حملات إعلانات ممولة' },
    ],
  },
];

const scrollToService = (id) => {
  activeFilter.value = id;
  const el = document.getElementById(id);
  if (el) {
    const yOffset = -100;
    const y = el.getBoundingClientRect().top + window.pageYOffset + yOffset;
    window.scrollTo({ top: y, behavior: 'smooth' });
  }
};
</script>

<template>
  <div class="services-view">
    <!-- Hero Section Matching Figma Frame 107 & Capability Chips -->
    <section class="services-hero">
      <div class="services-hero__bg">
        <img src="/assets/hero-bg.jpg" alt="خلفية خدمات سهم القمة" class="services-hero__bg-img" />
        <div class="services-hero__overlay"></div>
      </div>

      <div class="container services-hero__container">
        <div class="services-hero__content">
          <h1 class="services-hero__title">
            <span class="services-hero__title-line"><span class="highlight-red">خدمات</span> متكاملة</span>
            <span class="services-hero__title-line">لنجاح أعمالك</span>
          </h1>
          <p class="services-hero__desc">
            خدماتنا تغطي كل ما تحتاجه شركتك من التحليل حتى الانتشار الرقمي
          </p>
        </div>

        <!-- 5 Floating Services Pills Matching Figma -->
        <div class="services-pills">
          <button
            v-for="s in services"
            :key="s.id"
            class="services-pill"
            :class="{ 'services-pill--active': activeFilter === s.id }"
            @click="scrollToService(s.id)"
          >
            <span class="services-pill__dot" :style="{ backgroundColor: s.dotColor }"></span>
            <span class="services-pill__num">{{ s.number }}</span>
            <span class="services-pill__title">{{ s.pillTitle || s.title }}</span>
          </button>
        </div>
      </div>
    </section>

    <!-- Services Detailed List Matching Figma Node 303:649 -->
    <section class="services-list-section">
      <div
        v-for="s in services"
        :id="s.id"
        :key="s.id"
        class="service-item"
        :style="{ minHeight: s.minHeight }"
      >
        <!-- Giant background watermark with exact 20% alpha matching Figma -->
        <div
          class="service-item__giant-num"
          :style="{ color: s.watermarkColor }"
          aria-hidden="true"
        >
          {{ s.number }}
        </div>
        <div
          class="service-item__glow"
          :style="{ backgroundColor: s.accentColor }"
          aria-hidden="true"
        ></div>

        <div class="container">
          <!-- Top Divider Bar with Big Number, Line, and Watermark -->
          <div class="service-item__top-bar">
            <!-- Number and Line on the right (RTL: number on far right, line stretching to left) -->
            <span
              class="service-item__top-num"
              :style="{ color: s.accentColor }"
            >
              {{ s.number }}
            </span>
            <div
              class="service-item__top-line"
              :style="{ backgroundColor: s.lineColor }"
            ></div>
          </div>

          <div class="service-item__grid">
            <!-- Right Column in RTL: Description, Tools & Action Button -->
            <div class="service-item__info">
              <h2
                class="service-item__title"
                :style="{ color: s.titleColor }"
              >
                {{ s.title }}
              </h2>

              <div
                class="service-item__quote-wrap"
                :style="{ borderRightColor: s.accentColor }"
              >
                <p
                  class="service-item__quote"
                  :style="{ color: s.accentColor }"
                >
                  {{ s.quote }}
                </p>
              </div>

              <p class="service-item__desc">{{ s.desc }}</p>

              <!-- Tools used -->
              <div class="service-item__tools-wrap">
                <h4 class="service-item__tools-title">الأدوات المستخدمة</h4>
                <div class="service-item__tools-list">
                  <span
                    v-for="tool in s.tools"
                    :key="tool"
                    class="tool-chip"
                    :style="{ borderColor: s.accentColor }"
                  >
                    {{ tool }}
                  </span>
                </div>
              </div>

              <!-- Action Button -->
              <div class="service-item__action">
                <AppButton
                  :to="{ path: '/contact', query: { service: s.id } }"
                  :variant="s.btnVariant"
                  class="service-item__btn"
                  :style="{ backgroundColor: s.accentColor + ' !important' }"
                >
                  {{ s.btnText }}
                </AppButton>
              </div>
            </div>

            <!-- Left Column in RTL: Deliverables (ماذا نقدم) -->
            <div class="service-item__deliverables">
              <div class="deliverables-header">
                <span class="deliverables-header__title">ماذا نقدم</span>
                <span
                  class="deliverables-header__line"
                  :style="{ backgroundColor: s.lineColor }"
                ></span>
                <span class="deliverables-header__count">{{ s.deliverablesCount }}</span>
              </div>

              <div class="deliverables-grid">
                <div
                  v-for="(deliv, idx) in s.deliverables"
                  :key="deliv.id"
                  class="deliverable-chip"
                  :class="{ 'deliverable-chip--full': s.deliverables.length === 5 && idx === 4 }"
                  :style="{ borderColor: s.accentColor }"
                >
                  <span class="deliverable-chip__text">{{ deliv.text }}</span>
                  <span
                    class="deliverable-chip__num"
                    :style="{ color: s.accentColor }"
                  >
                    {{ deliv.id }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.services-view {
  position: relative;
  overflow-x: hidden;
  width: 100%;
}

.highlight-red {
  color: var(--color-primary);
}

/* Services Hero Matching Figma Frame 107 & Capability Chips */
.services-hero {
  position: relative;
  height: 100vh;
  min-height: 680px;
  max-height: 960px;
  display: flex;
  align-items: flex-end;
  padding-top: 130px;
  padding-bottom: 68px;
  overflow: hidden;
  box-sizing: border-box;
}

@media (max-width: 1024px) {
  .services-hero {
    height: auto;
    min-height: 100vh;
    padding-bottom: 48px;
  }
}

.services-hero__bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.services-hero__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
}

.services-hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    180deg,
    rgba(9, 22, 39, 0.72) 0%,
    rgba(9, 22, 39, 0.5) 40%,
    rgba(9, 22, 39, 0.88) 100%
  );
}

.services-hero__container {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  text-align: right;
  width: 100%;
  max-width: 1248px;
  height: 100%;
  padding-left: 0;
  padding-right: 0;
}

.services-hero__content {
  max-width: 636px;
  margin-top: auto;
  margin-bottom: auto;
  text-align: right;
}

.services-hero__title {
  font-size: 44px;
  font-weight: 800;
  color: #FFFFFF;
  margin-bottom: 24px;
  line-height: 1.2;
  display: flex;
  flex-direction: column;
  gap: 6px;
  text-align: right;
}

@media (min-width: 768px) {
  .services-hero__title {
    font-size: 58px;
    line-height: 1.18;
  }
}

@media (min-width: 1024px) {
  .services-hero__title {
    font-size: 72px;
    line-height: 82px;
  }
}

.services-hero__title-line {
  display: block;
}

.highlight-red {
  color: #D6214E;
}

.services-hero__desc {
  font-size: 18px;
  color: #C7C7C7;
  font-weight: 700;
  line-height: 1.6;
  max-width: 636px;
  text-align: right;
}

@media (min-width: 768px) {
  .services-hero__desc {
    font-size: 22px;
    line-height: 1.6;
  }
}

@media (min-width: 1024px) {
  .services-hero__desc {
    font-size: 28px;
    line-height: 42px;
  }
}

/* 5 Services Floating Glass Pills Matching Figma Frame 97 */
.services-pills {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 1248px;
  max-width: 100%;
  gap: 12px;
  flex-wrap: nowrap;
  margin-top: 24px;
  margin-bottom: 8px;
  background: transparent;
  border: none;
  padding: 0;
  box-shadow: none;
}

@media (max-width: 1247px) {
  .services-hero__container {
    padding-left: 20px;
    padding-right: 20px;
  }

  .services-pills {
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
    width: 100%;
  }
}

@media (max-width: 767px) {
  .services-hero {
    min-height: auto;
    padding-top: 120px;
    padding-bottom: 36px;
  }

  .services-hero__container {
    min-height: auto;
    gap: 20px;
  }

  .services-pills {
    flex-direction: column;
    align-items: stretch;
    width: 100%;
    gap: 10px;
    overflow-x: visible;
    flex-wrap: nowrap;
    margin-top: 24px;
    padding-bottom: 0;
  }

  .services-pill {
    width: 100%;
    justify-content: flex-start;
    padding: 12px 18px;
    border-radius: 14px;
    box-sizing: border-box;
  }

  .services-pill__title {
    font-size: 13px;
    white-space: normal;
    text-align: right;
  }
}

.services-pill {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  padding: 14px 35px;
  background: rgba(5, 10, 18, 0.85);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 26.5px;
  box-shadow: none;
  cursor: pointer;
  transition: all var(--transition-fast);
  direction: rtl;
  user-select: none;
  flex-shrink: 0;
}

.services-pill:hover {
  background: rgba(22, 38, 62, 0.92);
  border-color: rgba(255, 255, 255, 0.45);
  transform: translateY(-2px);
  box-shadow: none;
}

.services-pill--active {
  background: rgba(26, 45, 75, 0.95);
  border-color: rgba(255, 255, 255, 0.6);
  box-shadow: none;
}

.services-pill__dot {
  width: 8px;
  height: 8px;
  border-radius: 4px;
  flex-shrink: 0;
  box-shadow: none;
}

.services-pill__num {
  font-family: var(--font-inter);
  font-size: 10px;
  font-weight: 700;
  color: #9EABBA;
  line-height: 1;
}

.services-pill__title {
  font-size: 12px;
  font-weight: 700;
  color: #FFFFFF;
  white-space: nowrap;
  line-height: 1.2;
}

/* Detailed List matching Figma Node 303:649 & 303:650 */
.services-list-section {
  padding: 0;
  background-color: #FEFAF2;
  position: relative;
  overflow: hidden;
}

.services-list-section .container {
  max-width: 1248px;
  padding-left: 0;
  padding-right: 0;
}

@media (max-width: 1247px) {
  .services-list-section .container {
    padding-left: 20px;
    padding-right: 20px;
  }
}

.service-item {
  position: relative;
  width: 100%;
  padding: 40px 0 60px;
  overflow: hidden;
  display: flex;
  align-items: center;
}

@media (max-width: 767px) {
  .service-item {
    padding: 36px 0 50px;
    min-height: auto !important;
  }
}

/* Top Divider Bar */
.service-item__top-bar {
  display: flex;
  align-items: center;
  gap: 39px;
  position: relative;
  margin-bottom: 24px;
  direction: rtl;
  width: 100%;
}

@media (max-width: 767px) {
  .service-item__top-bar {
    gap: 16px;
    margin-bottom: 20px;
  }
}

.service-item__top-num {
  font-size: 80px;
  font-weight: 700;
  line-height: 1;
  font-family: var(--font-family);
  flex-shrink: 0;
  user-select: none;
}

@media (max-width: 767px) {
  .service-item__top-num {
    font-size: 56px;
    line-height: 1;
  }
}

@media (min-width: 768px) {
  .service-item__top-num {
    font-size: 110px;
    line-height: 1.2;
  }
}

@media (min-width: 1200px) {
  .service-item__top-num {
    font-size: 120px;
    line-height: 180px;
  }
}

.service-item__top-line {
  flex: 1;
  height: 1.5px;
  border-radius: 1px;
}

@media (min-width: 1200px) {
  .service-item__top-line {
    margin-left: 151px;
  }
}

/* Giant background watermark & glow at the very left of the screen */
.service-item__giant-num {
  position: absolute;
  top: 174px;
  left: -74px;
  font-size: 250px;
  font-weight: 700;
  line-height: 300px;
  letter-spacing: -0.05em;
  opacity: 1;
  user-select: none;
  pointer-events: none;
  font-family: var(--font-family);
  z-index: 0;
}

@media (max-width: 767px) {
  .service-item__giant-num {
    font-size: 110px;
    line-height: 130px;
    left: -20px;
    top: 10px;
  }
}

@media (min-width: 768px) and (max-width: 1199px) {
  .service-item__giant-num {
    font-size: 200px;
    line-height: 240px;
    left: -55px;
    top: 50px;
  }
}

.service-item__glow {
  position: absolute;
  top: 150px;
  left: 200px;
  width: 156px;
  height: 156px;
  border-radius: 50%;
  filter: blur(200px);
  opacity: 0.2;
  pointer-events: none;
  z-index: 0;
}

/* 2-Column Grid Side-by-Side */
.service-item__grid {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 1fr;
  gap: 40px;
  direction: rtl;
}

@media (min-width: 768px) {
  .service-item__grid {
    grid-template-columns: 1.15fr 1fr;
    gap: 36px;
    align-items: start;
  }
}

@media (min-width: 1200px) {
  .service-item__grid {
    grid-template-columns: 658px 486px;
    justify-content: space-between;
    gap: 104px;
  }
}

/* Right Column (Info) */
.service-item__info {
  display: flex;
  flex-direction: column;
  gap: 30px;
  align-items: flex-start;
  text-align: right;
  width: 100%;
}

.service-item__title {
  font-size: 34px;
  font-weight: 700;
  line-height: 1.35;
  margin: 0;
}

@media (min-width: 768px) {
  .service-item__title {
    font-size: 44px;
  }
}

@media (min-width: 1200px) {
  .service-item__title {
    font-size: 56px;
    line-height: 1.5;
  }
}

.service-item__quote-wrap {
  border-right: 2px solid;
  padding: 10px 14px 10px 0;
  margin: 0;
}

.service-item__quote {
  font-size: 20px;
  font-weight: 700;
  line-height: 1.5;
  margin: 0;
}

@media (min-width: 768px) {
  .service-item__quote {
    font-size: 24px;
  }
}

@media (min-width: 1200px) {
  .service-item__quote {
    font-size: 28px;
    line-height: 42px;
  }
}

.service-item__desc {
  font-size: 16px;
  color: #757575;
  line-height: 1.7;
  font-weight: 500;
  max-width: 455px;
  margin: 0;
}

@media (min-width: 768px) {
  .service-item__desc {
    font-size: 18px;
    line-height: 27px;
  }
}

/* Tools */
.service-item__tools-wrap {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 20px;
  width: 100%;
}

.service-item__tools-title {
  font-size: 18px;
  font-weight: 700;
  color: #616161;
  margin: 0;
}

.service-item__tools-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  direction: ltr;
  justify-content: flex-end;
  width: 100%;
}

.tool-chip {
  padding: 12px 16px;
  background-color: #FFF8F2;
  border: 1px solid;
  border-radius: 10px;
  font-size: 12px;
  font-weight: 700;
  color: #393C40;
  font-family: var(--font-family);
  text-align: left;
  transition: all var(--transition-fast);
}

.tool-chip:hover {
  transform: translateY(-2px);
}

.service-item__action {
  margin-top: 0;
  width: 100%;
}

.service-item__btn {
  width: 335px !important;
  max-width: 100%;
  height: 56px !important;
  border-radius: 10px !important;
  font-size: 16px !important;
  font-weight: 700 !important;
  color: #FFFFFF !important;
  box-shadow: none !important;
}

@media (max-width: 767px) {
  .service-item__btn {
    width: 100% !important;
    max-width: 100% !important;
  }
}

/* Left Column (Deliverables - ماذا نقدم) */
.service-item__deliverables {
  display: flex;
  flex-direction: column;
  gap: 54px;
  width: 100%;
}

@media (min-width: 1200px) {
  .service-item__deliverables {
    width: 486px;
    margin-top: 22px;
  }
}

.deliverables-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  direction: rtl;
  width: 100%;
  margin-bottom: 0;
}

.deliverables-header__title {
  font-size: 18px;
  font-weight: 700;
  color: #696969;
  white-space: nowrap;
  font-family: var(--font-family);
}

.deliverables-header__line {
  flex: 1;
  height: 1px;
  border-radius: 1px;
}

.deliverables-header__count {
  font-size: 20px;
  font-weight: 700;
  color: #696969;
  font-family: var(--font-family);
}

.deliverables-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
  width: 100%;
}

@media (min-width: 640px) {
  .deliverables-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px 16px;
  }
}

@media (min-width: 1200px) {
  .deliverables-grid {
    width: 486px;
    grid-template-columns: repeat(2, 230px);
    gap: 20px 26px;
  }
}

.deliverable-chip {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  min-height: 52px;
  padding: 14px 24px;
  background-color: #FFF8F2;
  border: 1px solid;
  border-radius: 20px;
  direction: rtl;
  transition: all var(--transition-fast);
  width: 100%;
}

.deliverable-chip--full {
  grid-column: 1 / -1;
  width: 100%;
}

.deliverable-chip:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.deliverable-chip__text {
  font-size: 12px;
  font-weight: 700;
  color: #6D6F73;
  font-family: var(--font-family);
  line-height: 14.4px;
}

.deliverable-chip__num {
  font-size: 10px;
  font-weight: 700;
  font-family: var(--font-inter);
  line-height: 12.1px;
  flex-shrink: 0;
}
</style>
