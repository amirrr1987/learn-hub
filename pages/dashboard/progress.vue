<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Progress Tracking</h1>
        <p class="text-lg text-gray-700">Track your progress across your courses and see how much you've accomplished.</p>
      </div>

      <!-- Progress Overview -->
      <div>
        <div v-if="coursesProgress.length">
          <ul class="space-y-8">
            <li v-for="course in coursesProgress" :key="course.id" class="border rounded-lg shadow-lg p-6">
              <h2 class="text-xl font-semibold mb-4">{{ course.title }}</h2>
              <p class="text-gray-600 mb-4">{{ course.description }}</p>
              <div class="relative">
                <div class="bg-gray-200 rounded-full h-4">
                  <div :style="{ width: course.progress + '%' }" class="bg-blue-600 h-4 rounded-full"></div>
                </div>
                <p class="absolute top-1/2 right-0 transform -translate-y-1/2 text-sm text-gray-600">{{ course.progress }}%</p>
              </div>
              <router-link :to="`/courses/${course.id}`" class="text-blue-600 hover:underline mt-4 block">
                View Course Details
              </router-link>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>You have no progress to show. Enroll in a course to start tracking your progress!</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

interface CourseProgress {
  id: number;
  title: string;
  description: string;
  progress: number; // Progress percentage
}

const coursesProgress = ref<CourseProgress[]>([]);

const fetchCoursesProgress = async () => {
  // Replace this with an actual API call
  const progressData: CourseProgress[] = [
    { id: 1, title: 'Introduction to Python', description: 'Start your journey with Python programming from scratch.', progress: 45 },
    { id: 2, title: 'HTML & CSS Essentials', description: 'Learn the foundational skills to create beautiful web pages.', progress: 70 }
  ];

  coursesProgress.value = progressData;
};

onMounted(() => {
  fetchCoursesProgress();
});
</script>
