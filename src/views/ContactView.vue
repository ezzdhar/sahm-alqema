<script setup>
import { ref, reactive, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import AppButton from '../components/common/AppButton.vue';
import InputField from '../components/common/InputField.vue';
import MainSelect from '../components/common/MainSelect.vue';

const route = useRoute();

const form = reactive({
  name: '',
  phone: '',
  email: '',
  service: '',
  details: '',
});

const errors = reactive({
  name: '',
  phone: '',
  email: '',
  service: '',
});

const isSubmitting = ref(false);
const isSubmitted = ref(false);

const serviceOptions = [
  { value: 'market-analysis', label: 'تحليل السوق والمنافسين' },
  { value: 'business-dev', label: 'تطوير الأعمال' },
  { value: 'web-apps', label: 'تصميم وبرمجة المواقع والتطبيقات' },
  { value: 'marketing', label: 'التسويق بالفيديو والجرافيك ديزاين' },
  { value: 'social-media', label: 'إدارة السوشيال ميديا' },
  { value: 'consulting', label: 'استشارة أعمال متكاملة' },
];

onMounted(() => {
  if (route.query.service) {
    const match = serviceOptions.find(o => o.value === route.query.service);
    if (match) {
      form.service = match.value;
    }
  }
});

const validateForm = () => {
  let valid = true;

  // Name
  if (!form.name.trim()) {
    errors.name = 'يرجى إدخال الاسم الكامل';
    valid = false;
  } else {
    errors.name = '';
  }

  // Phone
  if (!form.phone.trim()) {
    errors.phone = 'يرجى إدخال رقم الجوال';
    valid = false;
  } else if (!/^05\d{8}$/.test(form.phone.trim()) && form.phone.trim().length < 9) {
    errors.phone = 'يرجى إدخال رقم جوال صحيح (مثال: 05XXXXXXXX)';
    valid = false;
  } else {
    errors.phone = '';
  }

  // Email
  if (!form.email.trim()) {
    errors.email = 'يرجى إدخال البريد الإلكتروني';
    valid = false;
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email.trim())) {
    errors.email = 'يرجى إدخال بريد إلكتروني صالح';
    valid = false;
  } else {
    errors.email = '';
  }

  // Service
  if (!form.service) {
    errors.service = 'يرجى اختيار نوع الخدمة';
    valid = false;
  } else {
    errors.service = '';
  }

  return valid;
};

const handleSubmit = async () => {
  if (!validateForm()) return;

  isSubmitting.value = true;
  // Simulate API submission
  await new Promise(resolve => setTimeout(resolve, 900));
  isSubmitting.value = false;
  isSubmitted.value = true;

  // Reset form
  form.name = '';
  form.phone = '';
  form.email = '';
  form.service = '';
  form.details = '';
};
</script>

<template>
  <div class="contact-view">
    <!-- Hero Header -->
    <section class="contact-hero">
      <div class="contact-hero__bg">
        <img src="/assets/contact-page-bg.jpg" alt="خلفية مدينة الرياض" class="contact-hero__bg-img" />
        <div class="contact-hero__overlay"></div>
      </div>

      <div class="container contact-hero__container">
        <div class="contact-hero__content">
          <h1 class="contact-hero__title">
            <span class="highlight-red">ابدأ</span> مشروعك اليوم
          </h1>
          <p class="contact-hero__desc">
            تواصل معنا الآن وسيرد عليك فريقنا خلال 24 ساعة لمناقشة احتياجاتك وتقديم أفضل الحلول
          </p>
        </div>
      </div>
    </section>

    <!-- Main Card Section (Overlapping Hero) -->
    <section class="contact-main-section">
      <div class="container">
        <div class="contact-card">
          <!-- Right: Info Panel (Dark Blue) -->
          <div class="contact-info-panel">
            <div class="contact-info-panel__top">
              <h2 class="contact-info-panel__title">معلومات التواصل</h2>
              <p class="contact-info-panel__subtitle">
                نحن هنا للإجابة على استفساراتك ومساعدتك في تحقيق أهدافك الرقمية.
              </p>

              <div class="contact-info-list">
                <a href="tel:+966500000000" class="contact-info-item">
                  <span class="contact-info-icon" aria-hidden="true">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                    </svg>
                  </span>
                  <span class="contact-info-text" dir="ltr">+966 50 000 0000</span>
                </a>

                <a href="mailto:info@sahmaqemma.com" class="contact-info-item">
                  <span class="contact-info-icon" aria-hidden="true">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <rect x="2" y="4" width="20" height="16" rx="2"></rect>
                      <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"></path>
                    </svg>
                  </span>
                  <span class="contact-info-text">info@sahmaqemma.com</span>
                </a>

                <div class="contact-info-item">
                  <span class="contact-info-icon" aria-hidden="true">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"></path>
                      <circle cx="12" cy="10" r="3"></circle>
                    </svg>
                  </span>
                  <span class="contact-info-text">الرياض، المملكة العربية السعودية</span>
                </div>
              </div>
            </div>

            <!-- Why Choose Us List -->
            <div class="contact-why-us">
              <h3 class="contact-why-us__title">لماذا تختارنا؟</h3>
              <ul class="contact-why-us__list">
                <li class="contact-why-us__item">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#D6214E" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"></polyline>
                  </svg>
                  <span>استشارة مجانية بدون التزام</span>
                </li>
                <li class="contact-why-us__item">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#D6214E" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"></polyline>
                  </svg>
                  <span>تسليم في المواعيد المحددة</span>
                </li>
                <li class="contact-why-us__item">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#D6214E" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"></polyline>
                  </svg>
                  <span>فريق سعودي متخصص</span>
                </li>
                <li class="contact-why-us__item">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#D6214E" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"></polyline>
                  </svg>
                  <span>دعم مستمر ما بعد التسليم</span>
                </li>
              </ul>
            </div>
          </div>

          <!-- Left: Form Panel (White) -->
          <div class="contact-form-panel">
            <div v-if="isSubmitted" class="contact-success" role="alert">
              <div class="contact-success__icon">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
                  <polyline points="22 4 12 14.01 9 11.01"></polyline>
                </svg>
              </div>
              <h3 class="contact-success__title">تم إرسال طلبك بنجاح!</h3>
              <p class="contact-success__desc">
                شكرًا لتواصلك معنا. سنقوم بمراجعة طلبك والتواصل معك خلال 24 ساعة.
              </p>
              <AppButton variant="outline" size="md" @click="isSubmitted = false">
                إرسال طلب آخر
              </AppButton>
            </div>

            <form v-else class="contact-form" novalidate @submit.prevent="handleSubmit">
              <!-- Name and Phone Row -->
              <div class="contact-form__row">
                <InputField
                  v-model="form.name"
                  label="الاسم الكامل"
                  placeholder="أدخل اسمك الكامل"
                  required
                  :error="errors.name"
                />
                <InputField
                  v-model="form.phone"
                  label="رقم الجوال"
                  placeholder="05XXXXXXXX"
                  type="tel"
                  required
                  :error="errors.phone"
                />
              </div>

              <!-- Email -->
              <InputField
                v-model="form.email"
                label="البريد الإلكتروني"
                placeholder="example@company.com"
                type="email"
                required
                :error="errors.email"
              />

              <!-- Service Type -->
              <MainSelect
                v-model="form.service"
                label="نوع الخدمة المطلوبة"
                placeholder="اختر الخدمة المطلوبة"
                :options="serviceOptions"
                required
                :error="errors.service"
              />

              <!-- Project Details -->
              <InputField
                v-model="form.details"
                label="تفاصيل المشروع"
                placeholder="صف مشروعك ومتطلباتك بإيجاز..."
                is-textarea
                :rows="4"
              />

              <!-- Submit Button -->
              <div class="contact-form__submit">
                <AppButton
                  type="submit"
                  variant="primary"
                  size="lg"
                  block
                  :loading="isSubmitting"
                >
                  إرسال الطلب
                </AppButton>
              </div>
            </form>
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

.contact-view {
  background-color: var(--color-bg-light);
  min-height: 100vh;
}

/* Contact Hero */
.contact-hero {
  position: relative;
  min-height: 480px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 130px;
  padding-bottom: 120px;
  overflow: hidden;
  text-align: center;
}

.contact-hero__bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.contact-hero__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.contact-hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    180deg,
    rgba(9, 22, 39, 0.75) 0%,
    rgba(9, 22, 39, 0.6) 50%,
    rgba(9, 22, 39, 0.9) 100%
  );
}

.contact-hero__container {
  position: relative;
  z-index: 1;
}

.contact-hero__content {
  max-width: 760px;
  margin: 0 auto;
}

.contact-hero__title {
  font-size: 52px;
  font-weight: 800;
  color: #FFFFFF;
  margin-bottom: 16px;
}

@media (min-width: 768px) {
  .contact-hero__title {
    font-size: 64px;
  }
}

.contact-hero__desc {
  font-size: 20px;
  color: #E8ECF1;
  font-weight: 500;
  line-height: 1.6;
}

/* Main Overlapping Card */
.contact-main-section {
  position: relative;
  z-index: 10;
  margin-top: -80px;
  padding-bottom: 120px;
}

.contact-card {
  display: grid;
  grid-template-columns: 1fr;
  background: #FFFFFF;
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(9, 22, 39, 0.12);
  border: 1px solid #E8ECF1;
}

@media (min-width: 1024px) {
  .contact-card {
    grid-template-columns: 1fr 1.35fr;
  }
}

/* Info Panel (Dark Blue) */
.contact-info-panel {
  background: linear-gradient(145deg, #091627 0%, #102644 100%);
  color: #FFFFFF;
  padding: 50px 40px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 40px;
}

.contact-info-panel__title {
  font-size: 32px;
  font-weight: 800;
  margin-bottom: 12px;
  color: #FFFFFF;
}

.contact-info-panel__subtitle {
  font-size: 16px;
  color: #9EABBA;
  line-height: 1.6;
  margin-bottom: 36px;
}

.contact-info-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.contact-info-item {
  display: flex;
  align-items: center;
  gap: 16px;
  text-decoration: none;
  color: #FFFFFF;
  font-size: 16px;
  font-weight: 600;
  transition: transform var(--transition-fast);
}

.contact-info-item:hover {
  transform: translateX(-4px);
}

.contact-info-icon {
  width: 44px;
  height: 44px;
  border-radius: var(--radius-sm);
  background: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  box-shadow: 0 4px 12px rgba(214, 33, 78, 0.35);
}

.contact-why-us {
  border-top: 1px solid rgba(255, 255, 255, 0.12);
  padding-top: 30px;
}

.contact-why-us__title {
  font-size: 18px;
  font-weight: 700;
  color: #FFFFFF;
  margin-bottom: 16px;
}

.contact-why-us__list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.contact-why-us__item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  color: #CBD5E1;
  font-weight: 500;
}

/* Form Panel */
.contact-form-panel {
  padding: 50px 40px;
  display: flex;
  align-items: center;
  background-color: #FFFFFF;
}

@media (max-width: 640px) {
  .contact-form-panel {
    padding: 30px 20px;
  }
}

.contact-form {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.contact-form__row {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
}

@media (min-width: 640px) {
  .contact-form__row {
    grid-template-columns: repeat(2, 1fr);
  }
}

.contact-form__submit {
  margin-top: 8px;
}

/* Success Message */
.contact-success {
  text-align: center;
  padding: 40px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  width: 100%;
}

.contact-success__icon {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background-color: #F0FDF4;
  color: #16A34A;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 8px;
}

.contact-success__title {
  font-size: 26px;
  font-weight: 800;
  color: var(--color-navy-dark);
}

.contact-success__desc {
  font-size: 16px;
  color: var(--color-text-muted);
  max-width: 440px;
  line-height: 1.6;
  margin-bottom: 16px;
}
</style>
