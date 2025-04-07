<!-- Header Component Template -->
<template>
  <header class="bg-white shadow-sm sticky top-0 z-50">
    <div class="container mx-auto px-4 py-4 flex justify-between items-center">
      <router-link to="/" class="flex items-center space-x-2">
        <i class="fas fa-paw text-2xl text-blue-600"></i>
        <span class="text-xl font-bold text-blue-600">FurEver Home</span>
      </router-link>
      
      <nav class="hidden md:flex space-x-8">
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
        class="md:hidden text-gray-600 focus:outline-none"
      >
        <i class="fas fa-bars text-2xl"></i>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-if="mobileMenuOpen"
      class="md:hidden bg-white py-2 px-4 shadow-md"
    >
      <router-link
        v-for="link in links"
        :key="link.name"
        :to="link.path"
        class="block py-2 text-gray-700 hover:text-blue-600"
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