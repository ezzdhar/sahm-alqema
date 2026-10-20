<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { useRoute } from 'vue-router';
import AppButton from '../common/AppButton.vue';

const route = useRoute();
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

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true });
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});

const closeMobileMenu = () => {
  mobileMenuOpen.value = false;
};
</script>

<template>
  <header
    class="app-header"
    :class="{ 'app-header--scrolled': isScrolled, 'app-header--menu-open': mobileMenuOpen }"
  >
    <div class="container app-header__container">
      <div class="app-header__bar">
        <!-- Right: Logo -->
        <RouterLink to="/" class="app-header__logo" @click="closeMobileMenu">
          <img src="/assets/logo.png" alt="مؤسسة سهم القمة لتطوير وإدارة الأعمال" class="app-header__logo-img" />
        </RouterLink>

        <!-- Center: Navigation Links -->
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

          <button
            class="app-header__mobile-toggle"
            :aria-expanded="mobileMenuOpen"
            aria-label="تبديل القائمة"
            @click="mobileMenuOpen = !mobileMenuOpen"
          >
            <span class="hamburger-box">
              <span class="hamburger-inner" :class="{ 'is-active': mobileMenuOpen }"></span>
            </span>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Drawer -->
    <transition name="mobile-drawer">
      <div v-if="mobileMenuOpen" class="app-header__mobile-menu">
        <div class="app-header__mobile-links">
          <RouterLink
            v-for="link in navLinks"
            :key="link.path"
            :to="link.path"
            class="app-header__mobile-link"
            :class="{ 'app-header__mobile-link--active': route.path === link.path }"
            @click="closeMobileMenu"
          >
            {{ link.name }}
          </RouterLink>
          <div class="app-header__mobile-cta">
            <AppButton to="/contact" variant="primary" size="lg" block @click="closeMobileMenu">
              أبدأ الآن
            </AppButton>
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
  transition: all var(--transition-normal);
  background: transparent;
  pointer-events: none;
}

.app-header .container {
  pointer-events: auto;
}

.app-header--scrolled {
  padding: 12px 0 0;
}

.app-header__container {
  display: flex;
  justify-content: center;
}

/* Single Pill Header Bar matching Figma */
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
  background: rgba(9, 22, 39, 0.88);
  border-color: rgba(255, 255, 255, 0.18);
  box-shadow: 0 10px 32px rgba(0, 0, 0, 0.35);
  padding: 6px 20px 6px 10px;
}

/* Logo */
.app-header__logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  flex-shrink: 0;
}

.app-header__logo-img {
  height: 40px;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 2px 8px rgba(0, 0, 0, 0.3));
}

/* Nav Links */
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

@media (max-width: 767px) {
  .app-header__cta-btn {
    display: none;
  }
}

/* Mobile Toggle */
.app-header__mobile-toggle {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #FFFFFF;
  cursor: pointer;
}

@media (min-width: 768px) {
  .app-header__mobile-toggle {
    display: none;
  }
}

.hamburger-box {
  width: 20px;
  height: 16px;
  position: relative;
  display: block;
}

.hamburger-inner,
.hamburger-inner::before,
.hamburger-inner::after {
  width: 20px;
  height: 2px;
  background-color: #FFFFFF;
  border-radius: 2px;
  position: absolute;
  transition: all 0.25s ease;
}

.hamburger-inner {
  top: 50%;
  transform: translateY(-50%);
}

.hamburger-inner::before,
.hamburger-inner::after {
  content: '';
  left: 0;
}

.hamburger-inner::before {
  top: -6px;
}

.hamburger-inner::after {
  bottom: -6px;
}

.hamburger-inner.is-active {
  background-color: transparent;
}

.hamburger-inner.is-active::before {
  transform: translateY(6px) rotate(45deg);
}

.hamburger-inner.is-active::after {
  transform: translateY(-6px) rotate(-45deg);
}

/* Mobile Drawer */
.app-header__mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(9, 22, 39, 0.98);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  z-index: 1000;
  padding: 100px 24px 40px;
  display: flex;
  flex-direction: column;
}

.app-header__mobile-links {
  display: flex;
  flex-direction: column;
  gap: 16px;
  text-align: center;
  margin: auto 0;
}

.app-header__mobile-link {
  font-size: 20px;
  font-weight: 700;
  color: #E8ECF1;
  padding: 12px 20px;
  border-radius: var(--radius-md);
  transition: all var(--transition-fast);
}

.app-header__mobile-link:hover,
.app-header__mobile-link--active {
  color: var(--color-primary);
  background: rgba(214, 33, 78, 0.1);
}

.app-header__mobile-cta {
  margin-top: 24px;
}

/* Transitions */
.mobile-drawer-enter-active,
.mobile-drawer-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.mobile-drawer-enter-from,
.mobile-drawer-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
