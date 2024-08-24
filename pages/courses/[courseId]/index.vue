<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div v-if="course">
        <h1 class="text-3xl font-bold mb-4">{{ course.title }}</h1>
        <p class="text-gray-700 text-lg mb-6">{{ course.description }}</p>

        <div class="mb-8">
          <h2 class="text-2xl font-semibold mb-3">Instructor</h2>
          <p class="text-gray-700">{{ course.instructor }}</p>
        </div>

        <div>
          <h2 class="text-2xl font-semibold mb-3">Curriculum</h2>
          <ul class="list-disc list-inside space-y-2">
            <li v-for="(topic, index) in course.curriculum" :key="index">
              {{ topic }}
            </li>
          </ul>
        </div>
      </div>
      <div v-else>
        <p>Loading course details...</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

interface Course {
  id: number;
  title: string;
  description: string;
  instructor: string;
  curriculum: string[];
}

const route = useRoute();
const course = ref<Course | null>(null);

const fetchCourseDetails = async (id: number) => {
  // Replace this with an actual API call
  const courseData: Course = {
    id,
    title: 'Vue.js for Beginners',
    description: 'An introductory course to Vue.js, covering the basics of the framework and how to build single-page applications.',
    instructor: 'John Doe',
    curriculum: [
      'Introduction to Vue.js',
      'Data Binding and Directives',
      'Vue Components',
      'Handling Events',
      'Vue Router Basics',
      'State Management with Vuex',
      'Building a Complete Application'
    ]
  };
  
  course.value = courseData;
};

onMounted(() => {
  const courseId = parseInt(route.params.id as string, 10);
  fetchCourseDetails(courseId);
});
</script>

<style scoped>
.container {
  max-width: 800px;
}

h1, h2 {
  margin-bottom: 10px;
}

p {
  margin-bottom: 15px;
}

.list-disc {
  padding-left: 20px;
}
</style>
