<template>
  <header class="header">
    <div class="header-container">
      <router-link to="/" class="logo">
        <i class="fas fa-paw"></i>
        <span>FurEver Home</span>
      </router-link>
      
      <nav class="desktop-nav">
        <router-link 
          v-for="link in links" 
          :key="link.name"
          :to="link.path"
          class="nav-link"
        >
          {{ link.name }}
        </router-link>
      </nav>

      <button 
        @click="toggleMobileMenu"
        class="mobile-menu-button"
      >
        <i class="fas fa-bars"></i>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-if="mobileMenuOpen"
      class="mobile-menu"
    >
      <router-link
        v-for="link in links"
        :key="link.name"
        :to="link.path"
        class="mobile-nav-link"
        @click="mobileMenuOpen = false"
      >
        {{ link.name }}
      </router-link>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const links = [
  { name: 'Adopt', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Contact', path: '/contact' }
]

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}
</script>

<style scoped>
.header {
  background-color: white;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 50;
}

.header-container {
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
}

.logo i {
  font-size: 1.5rem;
  color: #2563eb;
}

.logo span {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2563eb;
}

.desktop-nav {
  display: none;
  gap: 2rem;
}

.nav-link {
  color: #374151;
  text-decoration: none;
  transition: color 0.2s;
}

.nav-link:hover {
  color: #2563eb;
}

.mobile-menu-button {
  color: #4b5563;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}

.mobile-menu-button i {
  font-size: 1.5rem;
}

.mobile-menu {
  background-color: white;
  padding: 0.5rem 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.mobile-nav-link {
  display: block;
  padding: 0.5rem 0;
  color: #374151;
  text-decoration: none;
}

.mobile-nav-link:hover {
  color: #2563eb;
}

.router-link-active {
  color: #2563eb;
  font-weight: 500;
}

@media (min-width: 768px) {
  .desktop-nav {
    display: flex;
  }
  
  .mobile-menu-button {
    display: none;
  }
}
</style>