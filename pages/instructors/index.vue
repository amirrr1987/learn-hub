<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <h1 class="text-3xl font-bold mb-6 text-center">Our Instructors</h1>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="instructor in instructors"
          :key="instructor.id"
          class="bg-white p-6 rounded-lg shadow-lg"
        >
          <img
            :src="instructor.photo"
            alt="Instructor Photo"
            class="w-32 h-32 object-cover rounded-full mx-auto mb-4 block"
          />
          <h2 class="text-xl font-semibold text-center mb-2">
            {{ instructor.name }}
          </h2>
          <p class="text-gray-700 text-center mb-4">{{ instructor.title }}</p>
          <p class="text-gray-600 text-center">{{ instructor.bio }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";

// Example instructor data
const instructors = ref([
  {
    id: 1,
    name: "John Doe",
    title: "Senior Instructor",
    bio: "Expert in programming with over 10 years of experience.",
    photo: "https://via.placeholder.com/150",
  },
  {
    id: 2,
    name: "Jane Smith",
    title: "Mathematics Expert",
    bio: "Passionate educator with a focus on applied mathematics.",
    photo: "https://via.placeholder.com/150",
  },
  {
    id: 3,
    name: "Emily Johnson",
    title: "Data Science Specialist",
    bio: "Specializes in data analysis and machine learning.",
    photo: "https://via.placeholder.com/150",
  },
  // Add more instructor data as needed
]);
</script>
