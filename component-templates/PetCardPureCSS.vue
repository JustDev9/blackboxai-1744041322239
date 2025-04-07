<template>
  <div class="pet-card">
    <img 
      :src="pet.image" 
      :alt="pet.name" 
      class="pet-image"
    >
    <div class="pet-info">
      <h3>{{ pet.name }}</h3>
      <div class="pet-details">
        <i class="fas fa-paw"></i>
        <span>{{ pet.breed }}</span>
      </div>
      <div class="pet-actions">
        <span class="pet-age">{{ pet.age }}</span>
        <button 
          @click="$emit('view-details', pet)"
          class="meet-button"
        >
          Meet {{ pet.name }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  pet: {
    type: Object,
    required: true
  }
})

defineEmits(['view-details'])
</script>

<style scoped>
.pet-card {
  background-color: white;
  border-radius: 0.75rem;
  overflow: hidden;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease;
}

.pet-card:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.pet-image {
  width: 100%;
  height: 12rem;
  object-fit: cover;
}

.pet-info {
  padding: 1rem;
}

.pet-info h3 {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #111827;
}

.pet-details {
  display: flex;
  align-items: center;
  color: #6b7280;
  margin-bottom: 1rem;
}

.pet-details i {
  margin-right: 0.5rem;
  color: #3b82f6;
}

.pet-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.pet-age {
  color: #3b82f6;
  font-weight: 500;
}

.meet-button {
  background-color: #e0e7ff;
  color: #3b82f6;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  font-weight: 500;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s;
}

.meet-button:hover {
  background-color: #c7d2fe;
}

@media (min-width: 640px) {
  .pet-image {
    height: 14rem;
  }
}

@media (min-width: 1024px) {
  .pet-image {
    height: 16rem;
  }
}
</style>