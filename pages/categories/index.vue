<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <h1 class="text-3xl font-bold mb-6 text-center">Categories</h1>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="category in categories" :key="category.id" class="bg-white p-6 rounded-lg shadow-lg">
          <h2 class="text-xl font-semibold mb-2">{{ category.name }}</h2>
          <p class="text-gray-700 mb-4">{{ category.description }}</p>
          <router-link :to="`/categories/${category.id}`" class="text-blue-600 hover:text-blue-800">
            View Courses
          </router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// Example category data
const categories = ref([
  {
    id: 1,
    name: 'Web Development',
    description: 'Courses on modern web development technologies including HTML, CSS, JavaScript, and frameworks.',
  },
  {
    id: 2,
    name: 'Data Science',
    description: 'Explore data analysis, machine learning, and statistical techniques for data-driven decision making.',
  },
  {
    id: 3,
    name: 'Design',
    description: 'Learn about graphic design, UI/UX design, and creative tools to create stunning visuals and user experiences.',
  },
  // Add more category data as needed
]);
</script>

