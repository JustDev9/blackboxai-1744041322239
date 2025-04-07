<!-- PetCard Component Template -->
<template>
  <div class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-lg transition">
    <img 
      :src="pet.image" 
      :alt="pet.name" 
      class="w-full h-48 object-cover"
    >
    <div class="p-4">
      <h3 class="text-xl font-semibold mb-1">{{ pet.name }}</h3>
      <div class="flex items-center text-gray-600 mb-2">
        <i class="fas fa-paw mr-2"></i>
        <span>{{ pet.breed }}</span>
      </div>
      <div class="flex justify-between items-center">
        <span class="text-blue-600 font-medium">{{ pet.age }}</span>
        <button 
          @click="$emit('view-details', pet)"
          class="bg-blue-100 text-blue-600 px-4 py-2 rounded-lg hover:bg-blue-200 transition"
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