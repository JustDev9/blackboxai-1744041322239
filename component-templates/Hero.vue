<!-- Hero Component Template -->
<template>
  <section class="hero bg-blue-50 py-16">
    <div class="container mx-auto px-4 text-center">
      <h1 class="text-4xl font-bold mb-6">Find Your Furry Friend</h1>
      
      <div class="max-w-2xl mx-auto bg-white p-6 rounded-lg shadow-md">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <select 
            v-model="filters.species" 
            class="p-3 border rounded-lg focus:ring-2 focus:ring-blue-500"
          >
            <option value="">All Pets</option>
            <option value="dog">Dogs</option>
            <option value="cat">Cats</option>
          </select>
          
          <button 
            @click="searchPets"
            class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition"
          >
            <i class="fas fa-search mr-2"></i>
            Search
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const filters = ref({
  species: '',
  breed: ''
})

const searchPets = () => {
  // Search logic will be implemented
}
</script>