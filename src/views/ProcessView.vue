<script setup>
import { ref } from 'vue';

const expandedStep = ref(null);

const toggleStep = (index) => {
  expandedStep.value = expandedStep.value === index ? null : index;
};

const steps = [
  {
    number: '01',
    title: 'اكتشاف',
    desc: 'نفهم نشاطك وأهدافك وتحدياتك الحالية. نحلل السوق والمنافسين، ونراجع كل ما هو متاح لديك حتى الآن.',
    deliverablesTitle: 'ماذا نقدم في هذه المرحلة',
    deliverablesCol1: [
      'جلسة استماع لفهم نشاطك وأهدافك',
      'مراجعة كل ما هو متاح لديك حاليًا (موقع، حسابات، مواد تسويقية)',
    ],
    deliverablesCol2: [
      'تحليل أولي للسوق والمنافسين المباشرين',
      'ملخص مكتوب بالفرص والتحديات الأساسية',
    ],
  },
  {
    number: '02',
    title: 'تخطيط',
    desc: 'نضع خارطة طريق واضحة بمراحل ومواعيد محددة، ونحدد أولويات التنفيذ حسب أهدافك.',
    deliverablesTitle: 'ماذا نقدم في هذه المرحلة',
    deliverablesCol1: [
      'خارطة طريق واضحة بمراحل ومواعيد محددة',
      'خطة تسعير وميزانية تقديرية لكل مرحلة',
    ],
    deliverablesCol2: [
      'تحديد الخدمات والأولويات المناسبة لهدفك',
      'مستند خطة عمل جاهز للمراجعة والموافقة',
    ],
  },
  {
    number: '03',
    title: 'تنفيذ',
    desc: 'يبدأ فريقنا العمل الفعلي بمتابعة أسبوعية، من التصميم والبرمجة إلى المحتوى والتسويق.',
    deliverablesTitle: 'ماذا نقدم في هذه المرحلة',
    deliverablesCol1: [
      'تنفيذ فعلي للخدمة المتفق عليها (تصميم، برمجة، محتوى)',
      'متابعة ومراجعات أسبوعية على تقدم العمل',
    ],
    deliverablesCol2: [
      'تحديد الخدمات والأولويات المناسبة لهدفك',
      'تواصل مباشر مع فريق العمل المسؤول عن مشروعك',
    ],
  },
  {
    number: '04',
    title: 'إطلاق',
    desc: 'نطلق مشروعك رسميًا وندير حضورك الرقمي، ونتابع الأداء بتقارير واضحة أولًا بأول.',
    deliverablesTitle: 'ماذا نقدم في هذه المرحلة',
    deliverablesCol1: [
      'تسليم نهائي للمشروع جاهزًا للانطلاق',
      'تقرير أداء أولي بعد الإطلاق مباشرة',
    ],
    deliverablesCol2: [
      'فتح وتجهيز الحسابات والمنصات المطلوبة',
      'خطة متابعة بعد التسليم (دعم أو تقارير دورية)',
    ],
  },
];
</script>

<template>
  <div class="process-view">
    <!-- Background Watermark Shield -->
    <div class="process-watermark" aria-hidden="true">
      <img src="/assets/shield-watermark.png" alt="" class="process-watermark__img" />
    </div>

    <div class="container process-container">
      <!-- Section Header -->
      <header class="process-header">
        <h1 class="process-header__title">
          من <span class="gradient-idea">الفكرة</span> إلى <span class="gradient-execution">التنفيذ</span>، بخطوات <span class="gradient-clear">واضحة</span>
        </h1>
        <p class="process-header__desc">
          خدماتنا تغطي كل ما تحتاجه شركتك من التحليل حتى الانتشار الرقمي
        </p>
      </header>

      <!-- Steps List -->
      <section class="process-list" aria-label="مراحل آلية العمل">
        <article
          v-for="(step, index) in steps"
          :key="step.number"
          class="process-item"
          :class="{ 'process-item--expanded': expandedStep === index }"
          tabindex="0"
          role="button"
          :aria-expanded="expandedStep === index"
          :aria-label="`مرحلة ${step.number}: ${step.title}`"
          @click="toggleStep(index)"
          @keydown.enter.prevent="toggleStep(index)"
          @keydown.space.prevent="toggleStep(index)"
        >
          <!-- Top Divider Line -->
          <div class="process-item__divider" aria-hidden="true"></div>

          <!-- Main Row -->
          <div class="process-item__row">
            <!-- Right: Number + Title -->
            <div class="process-item__heading">
              <span class="process-item__number">{{ step.number }}</span>
              <h2 class="process-item__title">{{ step.title }}</h2>
            </div>

            <!-- Middle: Description -->
            <div class="process-item__desc-wrap">
              <p class="process-item__desc">{{ step.desc }}</p>
            </div>

            <!-- Left: 65x65 Arrow Button -->
            <div class="process-item__action">
              <button
                type="button"
                class="process-item__arrow-btn"
                :aria-label="`تفاصيل مرحلة ${step.title}`"
                tabindex="-1"
              >
                <svg
                  width="65"
                  height="65"
                  viewBox="0 0 65 65"
                  fill="none"
                  class="process-item__arrow-svg"
                  aria-hidden="true"
                >
                  <circle
                    cx="32.5"
                    cy="32.5"
                    r="31"
                    class="arrow-circle"
                  />
                  <!-- Arrow pointing left (rotates to down when expanded) -->
                  <path
                    d="M41 32.5H24M31 24.5L23 32.5L31 40.5"
                    class="arrow-stem"
                    stroke-width="2.5"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>
              </button>
            </div>
          </div>

          <!-- Collapsible Drawer matching Figma Frame 124-127 -->
          <transition name="drawer">
            <div v-if="expandedStep === index" class="process-item__drawer">
              <div class="drawer-inner">
                <h3 class="drawer-title">{{ step.deliverablesTitle }}</h3>
                <div class="drawer-columns">
                  <!-- Col 1 (Right in RTL) -->
                  <div class="drawer-col">
                    <div
                      v-for="(item, iIdx) in step.deliverablesCol1"
                      :key="iIdx"
                      class="drawer-item"
                    >
                      <span class="drawer-bullet" aria-hidden="true"></span>
                      <span class="drawer-text">{{ item }}</span>
                    </div>
                  </div>

                  <!-- Col 2 (Left in RTL) -->
                  <div class="drawer-col">
                    <div
                      v-for="(item, iIdx) in step.deliverablesCol2"
                      :key="iIdx"
                      class="drawer-item"
                    >
                      <span class="drawer-bullet" aria-hidden="true"></span>
                      <span class="drawer-text">{{ item }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </transition>
        </article>

        <!-- Final Bottom Divider -->
        <div class="process-list__bottom-divider" aria-hidden="true"></div>
      </section>
    </div>
  </div>
</template>

<style scoped>
.process-view {
  background-color: #F5F0EC;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  padding: 210px 0 120px;
}

/* Background Watermark Shield */
.process-watermark {
  position: absolute;
  top: 80px;
  left: 50%;
  transform: translateX(-50%);
  width: 956px;
  max-width: 90vw;
  opacity: 0.5;
  pointer-events: none;
  z-index: 0;
}

.process-watermark__img {
  width: 100%;
  height: auto;
  display: block;
}

.process-container {
  position: relative;
  z-index: 1;
  max-width: 1248px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Header Aligned to Right */
.process-header {
  max-width: 568px;
  margin-right: 0;
  margin-left: auto;
  margin-bottom: 72px;
  text-align: right;
}

.process-header__title {
  font-family: var(--font-family);
  font-weight: 800;
  font-size: 56px;
  line-height: 84px;
  color: #040A12;
  margin-bottom: 20px;
  letter-spacing: -0.5px;
}

/* Word Gradients matching Figma styles ts1, ts2, ts3 */
.gradient-idea {
  background: linear-gradient(90deg, #D6214E 0%, #772851 72%, #142F54 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.gradient-execution {
  background: linear-gradient(90deg, #D6214E 0%, #142F54 46%, #772851 61%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.gradient-clear {
  background: linear-gradient(90deg, #D6214E 0%, #772851 42%, #142F54 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.process-header__desc {
  font-family: var(--font-family);
  font-weight: 700;
  font-size: 28px;
  line-height: 42px;
  color: #616161;
}

/* Steps List */
.process-list {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.process-item {
  width: 100%;
  cursor: pointer;
  outline: none;
  transition: background-color var(--transition-fast);
  border-radius: 12px;
}

.process-item:hover,
.process-item--expanded {
  background-color: rgba(255, 255, 255, 0.45);
}

.process-item:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 4px;
}

/* Divider Lines */
.process-item__divider,
.process-list__bottom-divider {
  width: 100%;
  height: 2px;
  background-color: #DBDBDB;
  transition: background-color var(--transition-normal);
}

.process-item:hover .process-item__divider,
.process-item--expanded .process-item__divider {
  background-color: #D6214E;
}

/* Main Row */
.process-item__row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
  padding: 28px 20px;
  transition: padding var(--transition-fast);
}

/* Heading: Number & Title */
.process-item__heading {
  display: flex;
  align-items: center;
  gap: 28px;
  flex-shrink: 0;
}

.process-item__number {
  font-family: var(--font-family);
  font-weight: 700;
  font-size: 90px;
  line-height: 1;
  color: #D6214E;
  user-select: none;
  min-width: 95px;
  text-align: right;
  transition: transform var(--transition-normal);
}

.process-item:hover .process-item__number,
.process-item--expanded .process-item__number {
  transform: scale(1.03);
}

.process-item__title {
  font-family: var(--font-family);
  font-weight: 800;
  font-size: 32px;
  line-height: 48px;
  color: #040A12;
  white-space: nowrap;
}

/* Middle: Description */
.process-item__desc-wrap {
  flex: 1;
  max-width: 568px;
}

.process-item__desc {
  font-family: var(--font-family);
  font-weight: 700;
  font-size: 24px;
  line-height: 36px;
  color: #616161;
  text-align: right;
  transition: color var(--transition-fast);
}

.process-item:hover .process-item__desc {
  color: #040A12;
}

/* Left: 65x65 Arrow Button */
.process-item__action {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.process-item__arrow-btn {
  width: 65px;
  height: 65px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  padding: 0;
  cursor: pointer;
}

.process-item__arrow-svg {
  width: 65px;
  height: 65px;
  display: block;
  transition: transform var(--transition-normal);
  transform-origin: center;
}

.arrow-circle {
  stroke: #D6214E;
  stroke-width: 1.5;
  fill: transparent;
  transition: stroke var(--transition-normal), fill var(--transition-normal);
}

.arrow-stem {
  stroke: #D6214E;
  transition: stroke var(--transition-normal);
}

/* Hover State */
.process-item:hover .arrow-circle {
  stroke: #D6214E;
  fill: #FBE9ED;
}

/* Expanded State: Solid red fill, white arrow, rotated to point down */
.process-item--expanded .arrow-circle,
.process-item--expanded:hover .arrow-circle {
  stroke: #D6214E;
  fill: #D6214E;
}

.process-item--expanded .arrow-stem,
.process-item--expanded:hover .arrow-stem {
  stroke: #FFFFFF;
}

.process-item--expanded .process-item__arrow-svg {
  transform: rotate(-90deg);
}

/* Collapsible Drawer matching Figma */
.process-item__drawer {
  overflow: hidden;
  padding: 0 20px 36px;
}

.drawer-inner {
  margin-right: 170px;
  max-width: 820px;
  padding-top: 4px;
}

.drawer-title {
  font-family: var(--font-family);
  font-size: 20px;
  font-weight: 700;
  color: #D6214E;
  margin-bottom: 18px;
  text-align: right;
}

.drawer-columns {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px 48px;
}

.drawer-col {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.drawer-item {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  text-align: right;
}

.drawer-bullet {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #D6214E;
  flex-shrink: 0;
  margin-top: 9px;
}

.drawer-text {
  font-family: var(--font-family);
  font-size: 17px;
  font-weight: 500;
  color: #4A4A4A;
  line-height: 1.6;
}

/* Transitions */
.drawer-enter-active,
.drawer-leave-active {
  transition: max-height 0.4s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.3s ease;
}

.drawer-enter-from,
.drawer-leave-to {
  max-height: 0;
  opacity: 0;
}

.drawer-enter-to,
.drawer-leave-from {
  max-height: 400px;
  opacity: 1;
}

/* Responsive Breakpoints */
@media (max-width: 1200px) {
  .process-header__title {
    font-size: 46px;
    line-height: 70px;
  }

  .process-header__desc {
    font-size: 24px;
    line-height: 36px;
  }

  .process-item__number {
    font-size: 76px;
  }

  .process-item__title {
    font-size: 28px;
  }

  .process-item__desc {
    font-size: 20px;
    line-height: 32px;
  }

  .drawer-inner {
    margin-right: 140px;
  }
}

@media (max-width: 900px) {
  .process-view {
    padding-top: 150px;
  }

  .process-header {
    margin-bottom: 48px;
  }

  .process-header__title {
    font-size: 38px;
    line-height: 58px;
  }

  .process-header__desc {
    font-size: 20px;
    line-height: 32px;
  }

  .process-item__row {
    display: grid;
    grid-template-columns: 1fr auto;
    grid-template-areas:
      "heading action"
      "desc desc";
    gap: 16px;
    padding: 20px 0;
    align-items: center;
  }

  .process-item__heading {
    grid-area: heading;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .process-item__action {
    grid-area: action;
    display: flex;
    justify-content: flex-end;
  }

  .process-item__desc-wrap {
    grid-area: desc;
    width: 100%;
    max-width: 100%;
    flex: none;
  }

  .process-item__desc {
    font-size: 16px;
    line-height: 26px;
  }

  .drawer-inner {
    margin-right: 0;
    max-width: 100%;
    padding-top: 12px;
  }
}

@media (max-width: 600px) {
  .process-header__title {
    font-size: 30px;
    line-height: 46px;
  }

  .process-header__desc {
    font-size: 18px;
    line-height: 28px;
  }

  .process-item__number {
    font-size: 56px;
    min-width: 60px;
  }

  .process-item__title {
    font-size: 24px;
    line-height: 36px;
  }

  .process-item__desc {
    font-size: 17px;
    line-height: 28px;
  }

  .process-item__arrow-btn,
  .process-item__arrow-svg {
    width: 52px;
    height: 52px;
  }

  .drawer-columns {
    grid-template-columns: 1fr;
    gap: 14px;
  }
}
</style>
