<!-- Contact View Template -->
<template>
  <div>
    <section class="hero bg-gradient-to-br from-blue-50 to-purple-50 py-16">
      <div class="container mx-auto px-4 text-center">
        <h1 class="text-4xl font-bold mb-4">Get In Touch</h1>
        <p class="text-xl text-gray-600">
          We'd love to hear from you! Reach out with any questions.
        </p>
      </div>
    </section>

    <section class="container mx-auto px-4 py-12">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
        <div>
          <h2 class="text-3xl font-bold mb-6">Contact Form</h2>
          <form @submit.prevent="submitForm" class="space-y-4">
            <div>
              <label for="name" class="block text-gray-700 mb-2">Name</label>
              <input
                type="text"
                id="name"
                v-model="form.name"
                class="w-full p-3 border rounded-lg"
                required
              >
            </div>
            
            <div>
              <label for="email" class="block text-gray-700 mb-2">Email</label>
              <input
                type="email"
                id="email"
                v-model="form.email"
                class="w-full p-3 border rounded-lg"
                required
              >
            </div>
            
            <button
              type="submit"
              class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition"
            >
              Send Message
            </button>
          </form>
        </div>
        
        <div>
          <h2 class="text-3xl font-bold mb-6">Our Location</h2>
          <div class="bg-white p-6 rounded-lg shadow-sm">
            <div class="flex items-start mb-6">
              <i class="fas fa-map-marker-alt text-blue-600 text-xl mt-1 mr-4"></i>
              <div>
                <h3 class="text-lg font-semibold">Headquarters</h3>
                <p class="text-gray-600">123 Pet Lane, Animal City</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  // Form submission logic
}
</script>