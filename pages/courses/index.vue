<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <h1 class="text-3xl font-bold mb-8">Our Courses</h1>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="course in courses" :key="course.id" class="border p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow duration-300">
          <h2 class="text-xl font-semibold mb-4">{{ course.title }}</h2>
          <p class="mb-4">{{ course.description }}</p>
          <router-link :to="'/courses/' + course.id" class="text-blue-600 hover:underline">Learn More</router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// Define the course type
interface Course {
  id: number;
  title: string;
  description: string;
}

// Sample data for courses
const courses = ref<Course[]>([
  { id: 1, title: 'Introduction to Web Development', description: 'Learn the basics of HTML, CSS, and JavaScript.' },
  { id: 2, title: 'Advanced JavaScript', description: 'Dive deeper into JavaScript with ES6 features and beyond.' },
  { id: 3, title: 'Vue.js for Beginners', description: 'Get started with Vue.js and build your first web application.' },
  { id: 4, title: 'Mastering TypeScript', description: 'Learn TypeScript and how to apply it to large-scale JavaScript applications.' },
  { id: 5, title: 'React Fundamentals', description: 'Understand the core concepts of React and build dynamic UIs.' },
  { id: 6, title: 'Node.js Essentials', description: 'Build scalable backend applications using Node.js and Express.' }
]);

</script>

<style scoped>
.container {
  max-width: 1200px;
}

h1 {
  text-align: center;
}

.grid {
  display: grid;
}

.border {
  border: 1px solid #e2e8f0;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.shadow-md {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.hover\:shadow-lg:hover {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.transition-shadow {
  transition: box-shadow 0.3s ease-in-out;
}
</style>
