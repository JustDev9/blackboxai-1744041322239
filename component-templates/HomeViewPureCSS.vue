<template>
  <div class="home-view">
    <HeroPureCSS @search="handleSearch" />
    <section class="pets-section">
      <h2>Available Pets</h2>
      
      <div v-if="loading" class="loading-state">
        <i class="fas fa-spinner fa-spin"></i>
      </div>
      
      <div v-else>
        <div v-if="filteredPets.length > 0" class="pets-grid">
          <PetCardPureCSS 
            v-for="pet in filteredPets" 
            :key="pet.id" 
            :pet="pet"
            @view-details="viewPetDetails"
          />
        </div>
        
        <div v-else class="empty-state">
          <i class="fas fa-paw"></i>
          <h3>No pets found matching your criteria</h3>
          <button 
            @click="resetFilters"
            class="reset-button"
          >
            Reset filters
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import HeroPureCSS from './HeroPureCSS.vue'
import PetCardPureCSS from './PetCardPureCSS.vue'

const pets = ref([])
const loading = ref(true)
const filters = ref({
  species: '',
  breed: ''
})

// Sample pet data
const samplePets = [
  {
    id: 1,
    name: 'Buddy',
    breed: 'Golden Retriever',
    age: '2 years',
    species: 'dog',
    image: 'https://images.pexels.com/photos/1640109/pexels-photo-1640109.jpeg'
  },
  {
    id: 2,
    name: 'Whiskers',
    breed: 'Siamese',
    age: '1 year',
    species: 'cat',
    image: 'https://images.pexels.com/photos/1205393/pexels-photo-1205393.jpeg'
  }
]

onMounted(() => {
  // Simulate API call
  setTimeout(() => {
    pets.value = samplePets
    loading.value = false
  }, 1000)
})

const filteredPets = computed(() => {
  if (!filters.value.species && !filters.value.breed) {
    return pets.value
  }
  
  return pets.value.filter(pet => {
    const speciesMatch = !filters.value.species || pet.species === filters.value.species
    const breedMatch = !filters.value.breed || pet.breed === filters.value.breed
    return speciesMatch && breedMatch
  })
})

const handleSearch = (searchFilters) => {
  filters.value = { ...searchFilters }
}

const viewPetDetails = (pet) => {
  console.log('Viewing details for:', pet)
}

const resetFilters = () => {
  filters.value = { species: '', breed: '' }
}
</script>

<style scoped>
.home-view {
  min-height: 100vh;
}

.pets-section {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 3rem 1rem;
}

.pets-section h2 {
  font-size: 1.875rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 2rem;
  color: #1e3a8a;
}

.loading-state {
  text-align: center;
  padding: 3rem 0;
}

.loading-state i {
  font-size: 2.5rem;
  color: #3b82f6;
}

.pets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.empty-state {
  text-align: center;
  padding: 3rem 0;
}

.empty-state i {
  font-size: 2.5rem;
  color: #9ca3af;
  margin-bottom: 1rem;
}

.empty-state h3 {
  font-size: 1.25rem;
  font-weight: 500;
  color: #6b7280;
  margin-bottom: 1.5rem;
}

.reset-button {
  color: #3b82f6;
  background: none;
  border: none;
  font-size: 1rem;
  cursor: pointer;
  text-decoration: underline;
}

.reset-button:hover {
  color: #2563eb;
}

@media (min-width: 768px) {
  .pets-section {
    padding: 3rem 2rem;
  }
}
</style>