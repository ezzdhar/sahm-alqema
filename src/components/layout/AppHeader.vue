<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import AppButton from '../common/AppButton.vue';

const route = useRoute();
const baseUrl = import.meta.env.BASE_URL;
const isScrolled = ref(false);
const mobileMenuOpen = ref(false);

const navLinks = [
  { name: 'الرئيسية', path: '/' },
  { name: 'خدماتنا', path: '/services' },
  { name: 'آلية العمل', path: '/process' },
  { name: 'من نحن', path: '/about' },
  { name: 'تواصل معنا', path: '/contact' },
];

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20;
};

const closeMobileMenu = () => {
  mobileMenuOpen.value = false;
};

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

// Auto close mobile drawer on route change
watch(
  () => route.path,
  () => {
    closeMobileMenu();
  }
);

// Prevent body scroll when drawer is open
watch(mobileMenuOpen, (isOpen) => {
  if (typeof document !== 'undefined') {
    if (isOpen) {
      document.body.style.overflow = 'hidden';
    } else {
      document.body.style.overflow = '';
    }
  }
});

// Close drawer on window resize to desktop
const handleResize = () => {
  if (window.innerWidth >= 768 && mobileMenuOpen.value) {
    closeMobileMenu();
  }
};

// Close on Escape key press
const handleKeydown = (e) => {
  if (e.key === 'Escape' && mobileMenuOpen.value) {
    closeMobileMenu();
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true });
  window.addEventListener('resize', handleResize, { passive: true });
  window.addEventListener('keydown', handleKeydown);
});

onUnmounted(() => {
  if (typeof document !== 'undefined') {
    document.body.style.overflow = '';
  }
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('resize', handleResize);
  window.removeEventListener('keydown', handleKeydown);
});
</script>

<template>
  <header
    class="app-header"
    :class="{
      'app-header--scrolled': isScrolled,
      'app-header--menu-open': mobileMenuOpen
    }"
  >
    <div class="container app-header__container">
      <div class="app-header__bar">
        <!-- Right: Logo (in RTL, first visual item on right) -->
        <RouterLink to="/" class="app-header__logo" @click="closeMobileMenu">
          <img
            :src="`${baseUrl}assets/logo.png`"
            alt="مؤسسة سهم القمة لتطوير وإدارة الأعمال"
            class="app-header__logo-img"
          />
        </RouterLink>

        <!-- Center: Desktop Navigation Links -->
        <nav class="app-header__nav" aria-label="القائمة الرئيسية">
          <RouterLink
            v-for="link in navLinks"
            :key="link.path"
            :to="link.path"
            class="app-header__nav-link"
            :class="{ 'app-header__nav-link--active': route.path === link.path }"
          >
            {{ link.name }}
            <span v-if="route.path === link.path" class="app-header__active-underline"></span>
          </RouterLink>
        </nav>

        <!-- Left: CTA Button & Mobile Toggle -->
        <div class="app-header__actions">
          <AppButton to="/contact" variant="primary" size="md" class="app-header__cta-btn">
            أبدأ الآن
          </AppButton>

          <!-- Mobile Burger Toggle Button -->
          <button
            type="button"
            class="app-header__mobile-toggle"
            :class="{ 'app-header__mobile-toggle--open': mobileMenuOpen }"
            :aria-expanded="mobileMenuOpen"
            aria-label="تبديل القائمة"
            aria-controls="mobile-menu-drawer"
            @click="toggleMobileMenu"
          >
            <span class="hamburger-box" aria-hidden="true">
              <transition name="icon-fade" mode="out-in">
                <!-- Symmetrical centered 3-line hamburger icon -->
                <svg
                  v-if="!mobileMenuOpen"
                  key="menu"
                  class="hamburger-icon"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2.3"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <line x1="4" y1="6" x2="20" y2="6" />
                  <line x1="4" y1="12" x2="20" y2="12" />
                  <line x1="4" y1="18" x2="20" y2="18" />
                </svg>

                <!-- Symmetrical centered close (X) icon -->
                <svg
                  v-else
                  key="close"
                  class="hamburger-icon"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2.3"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <line x1="6" y1="6" x2="18" y2="18" />
                  <line x1="6" y1="18" x2="18" y2="6" />
                </svg>
              </transition>
            </span>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Drawer Overlay & Menu -->
    <transition name="mobile-drawer">
      <div
        v-if="mobileMenuOpen"
        id="mobile-menu-drawer"
        class="app-header__mobile-menu"
        role="dialog"
        aria-modal="true"
        aria-label="القائمة المتنقلة"
        @click.self="closeMobileMenu"
      >
        <div class="app-header__mobile-content">
          <nav class="app-header__mobile-nav" aria-label="روابط القائمة الرئيسية">
            <RouterLink
              v-for="link in navLinks"
              :key="link.path"
              :to="link.path"
              class="app-header__mobile-link"
              :class="{ 'app-header__mobile-link--active': route.path === link.path }"
              @click="closeMobileMenu"
            >
              <span class="app-header__mobile-link-text">{{ link.name }}</span>
              <span class="app-header__mobile-link-arrow" aria-hidden="true">‹</span>
            </RouterLink>
          </nav>

          <div class="app-header__mobile-cta">
            <AppButton to="/contact" variant="primary" size="lg" block @click="closeMobileMenu">
              أبدأ الآن
            </AppButton>
          </div>

          <div class="app-header__mobile-footer">
            <div class="app-header__mobile-tagline">مؤسسة سهم القمة لتطوير وإدارة الأعمال</div>
            <div class="app-header__mobile-sub">حلول استشارية واستثمارية متكاملة</div>
          </div>
        </div>
      </div>
    </transition>
  </header>
</template>

<style scoped>
.app-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 24px 0 0;
  transition: padding var(--transition-normal);
  background: transparent;
  pointer-events: none;
}

.app-header--menu-open {
  pointer-events: auto;
}

.app-header .container {
  pointer-events: auto;
  position: relative;
  z-index: 1002;
}

.app-header--scrolled {
  padding: 12px 0 0;
}

.app-header__container {
  display: flex;
  justify-content: center;
}

/* Single Pill Header Bar */
.app-header__bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  gap: 24px;
  background: rgba(9, 22, 39, 0.45);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.35);
  border-radius: var(--radius-full);
  padding: 8px 24px 8px 12px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
  transition: all var(--transition-normal);
}

.app-header--scrolled .app-header__bar {
  background: rgba(9, 22, 39, 0.9);
  border-color: rgba(255, 255, 255, 0.18);
  box-shadow: 0 10px 32px rgba(0, 0, 0, 0.35);
  padding: 6px 20px 6px 10px;
}

.app-header--menu-open .app-header__bar {
  background: rgba(9, 22, 39, 0.95);
  border-color: rgba(255, 255, 255, 0.22);
  box-shadow: 0 12px 36px rgba(0, 0, 0, 0.4);
}

/* Logo */
.app-header__logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  flex-shrink: 0;
}

.app-header__logo-img {
  height: 44px;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 2px 8px rgba(0, 0, 0, 0.3));
  transition: height var(--transition-fast);
}

/* Nav Links (Desktop) */
.app-header__nav {
  display: none;
  align-items: center;
  gap: 16px;
}

@media (min-width: 768px) {
  .app-header__nav {
    display: flex;
  }
}

@media (min-width: 1024px) {
  .app-header__nav {
    gap: 28px;
  }
}

.app-header__nav-link {
  position: relative;
  font-size: 14px;
  font-weight: 500;
  color: #E8ECF1;
  text-decoration: none;
  padding: 8px 4px;
  transition: color var(--transition-fast);
  white-space: nowrap;
}

@media (min-width: 1024px) {
  .app-header__nav-link {
    font-size: 16px;
  }
}

.app-header__nav-link:hover {
  color: #FFFFFF;
}

.app-header__nav-link--active {
  color: #FFFFFF;
  font-weight: 700;
}

.app-header__active-underline {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 2px;
  background-color: #FFFFFF;
  border-radius: 2px;
}

/* Actions */
.app-header__actions {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-shrink: 0;
}

.app-header__cta-btn {
  border-radius: 12px !important;
  font-weight: 700;
  padding: 8px 18px;
  font-size: 14px;
  box-shadow: 0 4px 14px rgba(214, 33, 78, 0.4);
}

@media (min-width: 1024px) {
  .app-header__cta-btn {
    padding: 10px 24px;
    font-size: 15px;
  }
}

/* Mobile Burger Toggle Button */
.app-header__mobile-toggle {
  display: none;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  min-width: 40px;
  min-height: 40px;
  padding: 0;
  margin: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.22);
  color: #FFFFFF;
  cursor: pointer;
  outline: none;
  box-sizing: border-box;
  transition: all var(--transition-fast);
  -webkit-tap-highlight-color: transparent;
  flex-shrink: 0;
}

.app-header__mobile-toggle:hover {
  background: rgba(255, 255, 255, 0.16);
  border-color: rgba(255, 255, 255, 0.38);
}

.app-header__mobile-toggle:active {
  transform: scale(0.92);
}

.app-header__mobile-toggle--open {
  background: rgba(214, 33, 78, 0.25);
  border-color: rgba(214, 33, 78, 0.7);
  box-shadow: 0 0 12px rgba(214, 33, 78, 0.35);
}

.hamburger-box {
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  line-height: 0;
}

.hamburger-icon {
  width: 20px;
  height: 20px;
  display: block;
  overflow: visible;
}

/* Smooth Icon Transition (Burger <-> Close) */
.icon-fade-enter-active,
.icon-fade-leave-active {
  transition: opacity 0.18s ease, transform 0.18s ease;
}

.icon-fade-enter-from {
  opacity: 0;
  transform: rotate(-90deg) scale(0.75);
}

.icon-fade-leave-to {
  opacity: 0;
  transform: rotate(90deg) scale(0.75);
}

/* Mobile Drawer */
.app-header__mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100vh;
  height: 100dvh;
  background: linear-gradient(180deg, rgba(7, 18, 33, 0.98) 0%, rgba(10, 24, 43, 0.99) 100%);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  z-index: 1001;
  pointer-events: auto;
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  display: flex;
  flex-direction: column;
  padding: 88px 20px 32px;
}

.app-header__mobile-content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: calc(100dvh - 120px);
  max-width: 480px;
  width: 100%;
  margin: 0 auto;
}

.app-header__mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.app-header__mobile-link {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 17px;
  font-weight: 600;
  color: #E8ECF1;
  padding: 14px 18px;
  border-radius: var(--radius-md);
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  transition: all var(--transition-fast);
  text-decoration: none;
}

.app-header__mobile-link:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.16);
  color: #FFFFFF;
}

.app-header__mobile-link--active {
  background: rgba(214, 33, 78, 0.15);
  border-color: rgba(214, 33, 78, 0.4);
  color: #FFFFFF;
  font-weight: 700;
}

.app-header__mobile-link-arrow {
  color: var(--color-text-light);
  font-size: 22px;
  line-height: 1;
  transition: transform var(--transition-fast), color var(--transition-fast);
}

.app-header__mobile-link:hover .app-header__mobile-link-arrow,
.app-header__mobile-link--active .app-header__mobile-link-arrow {
  color: var(--color-primary);
  transform: translateX(-4px);
}

.app-header__mobile-cta {
  margin-top: 24px;
}

.app-header__mobile-footer {
  margin-top: 24px;
  padding-top: 20px;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  text-align: center;
}

.app-header__mobile-tagline {
  font-size: 13px;
  font-weight: 700;
  color: #FFFFFF;
  margin-bottom: 4px;
}

.app-header__mobile-sub {
  font-size: 12px;
  color: var(--color-text-light);
}

/* Mobile Drawer Transitions */
.mobile-drawer-enter-active,
.mobile-drawer-leave-active {
  transition: opacity 0.28s cubic-bezier(0.16, 1, 0.3, 1), transform 0.28s cubic-bezier(0.16, 1, 0.3, 1);
}

.mobile-drawer-enter-from,
.mobile-drawer-leave-to {
  opacity: 0;
  transform: translateY(-12px);
}

/* Responsive Breakpoints */
@media (max-width: 767px) {
  .app-header {
    padding: 12px 0 0;
  }

  .app-header--scrolled {
    padding: 8px 0 0;
  }

  .app-header .container {
    padding-left: 16px;
    padding-right: 16px;
  }

  .app-header__bar {
    padding: 6px 14px 6px 14px;
    gap: 12px;
  }

  .app-header--scrolled .app-header__bar {
    padding: 5px 12px 5px 12px;
  }

  .app-header__logo-img {
    height: 36px;
  }

  .app-header__cta-btn {
    display: none;
  }

  .app-header__mobile-toggle {
    display: inline-flex;
  }
}

@media (min-width: 768px) and (max-width: 1023px) {
  .app-header__bar {
    padding: 8px 16px;
    gap: 14px;
  }

  .app-header__nav {
    gap: 14px;
  }

  .app-header__nav-link {
    font-size: 13.5px;
    padding: 6px 2px;
  }

  .app-header__cta-btn {
    padding: 8px 14px;
    font-size: 13px;
  }

  .app-header__logo-img {
    height: 38px;
  }
}
</style>
