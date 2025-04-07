<template>
  <section class="hero">
    <div class="hero-container">
      <h1>Find Your Furry Friend</h1>
      <p>Discover your perfect pet companion from our loving shelter animals</p>
      
      <div class="search-container">
        <div class="search-grid">
          <select v-model="filters.species" class="search-select">
            <option value="">All Pets</option>
            <option value="dog">Dogs</option>
            <option value="cat">Cats</option>
            <option value="rabbit">Rabbits</option>
          </select>
          
          <select 
            v-model="filters.breed" 
            class="search-select"
            :disabled="!filters.species"
          >
            <option value="">All Breeds</option>
            <option 
              v-for="breed in filteredBreeds" 
              :key="breed"
              :value="breed"
            >
              {{ breed }}
            </option>
          </select>
          
          <button 
            @click="searchPets"
            class="search-button"
          >
            <i class="fas fa-search"></i>
            Search
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const filters = ref({
  species: '',
  breed: '',
  location: ''
})

const breeds = {
  dog: ['Labrador', 'German Shepherd', 'Beagle', 'Poodle'],
  cat: ['Siamese', 'Persian', 'Maine Coon', 'Bengal'],
  rabbit: ['Holland Lop', 'Mini Rex', 'Flemish Giant']
}

const filteredBreeds = computed(() => {
  return filters.value.species ? breeds[filters.value.species] : []
})

const searchPets = () => {
  console.log('Searching with filters:', filters.value)
}
</script>

<style scoped>
.hero {
  background-color: #eff6ff;
  background-image: linear-gradient(to bottom, rgba(239, 246, 255, 0.9), rgba(219, 234, 254, 0.9));
  padding: 4rem 0;
  text-align: center;
}

.hero-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.hero h1 {
  font-size: 2.25rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: #1e3a8a;
}

.hero p {
  font-size: 1.25rem;
  color: #4b5563;
  margin-bottom: 2rem;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
}

.search-container {
  background-color: white;
  padding: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
  max-width: 42rem;
  margin: 0 auto;
}

.search-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

.search-select {
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  width: 100%;
  font-size: 1rem;
}

.search-select:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.5);
}

.search-button {
  background-color: #2563eb;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 0.375rem;
  font-size: 1rem;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  cursor: pointer;
  border: none;
  transition: background-color 0.2s;
}

.search-button:hover {
  background-color: #1d4ed8;
}

.search-button i {
  font-size: 1rem;
}

@media (min-width: 768px) {
  .search-grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .hero h1 {
    font-size: 2.5rem;
  }
}
</style>