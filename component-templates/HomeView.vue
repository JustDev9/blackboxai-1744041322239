<!-- Home View Template -->
<template>
  <div>
    <Hero @search="handleSearch" />
    <section class="container mx-auto px-4 py-12">
      <h2 class="text-3xl font-bold mb-8 text-center">Available Pets</h2>
      
      <div v-if="loading" class="text-center py-12">
        <i class="fas fa-spinner fa-spin text-4xl text-blue-600"></i>
      </div>
      
      <div v-else>
        <div v-if="filteredPets.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <PetCard 
            v-for="pet in filteredPets" 
            :key="pet.id" 
            :pet="pet"
            @view-details="viewPetDetails"
          />
        </div>
        
        <div v-else class="text-center py-12">
          <h3 class="text-xl font-medium text-gray-600">No pets found</h3>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import Hero from '@/components/Hero.vue'
import PetCard from '@/components/PetCard.vue'

const pets = ref([])
const loading = ref(true)
const filters = ref({
  species: '',
  breed: ''
})

// Sample data - will replace with API call
setTimeout(() => {
  pets.value = [
    {
      id: 1,
      name: 'Buddy',
      breed: 'Golden Retriever',
      age: '2 years',
      image: 'https://images.pexels.com/photos/1640109/pexels-photo-1640109.jpeg'
    }
  ]
  loading.value = false
}, 1000)

const filteredPets = computed(() => {
  // Filter logic here
  return pets.value
})

const handleSearch = (searchFilters) => {
  filters.value = searchFilters
}

const viewPetDetails = (pet) => {
  // Navigation logic
}
</script>