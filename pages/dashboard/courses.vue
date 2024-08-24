<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">My Courses</h1>
        <p class="text-lg text-gray-700">
          Here is a list of courses you are currently enrolled in. Click on a
          course to continue learning or view details.
        </p>
      </div>

      <!-- Enrolled Courses -->
      <div>
        <div v-if="courses.length">
          <ul class="list-none grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <li
              v-for="course in courses"
              :key="course.id"
              class="border rounded-lg shadow-lg p-6"
            >
              <h3 class="text-xl font-semibold mb-4">{{ course.title }}</h3>
              <p class="text-gray-600 mb-4">{{ course.description }}</p>
              <div class="flex justify-between items-center">
                <NuxtLink
                  :to="`/courses/${course.id}`"
                  class="text-blue-600 hover:underline"
                >
                  View Course
                </NuxtLink>
                <button
                  class="px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition"
                >
                  Continue Learning
                </button>
              </div>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>
            You are not enrolled in any courses yet. Explore our
            <NuxtLink to="/courses" class="text-blue-600 hover:underline"
              >course catalog</NuxtLink
            >
            to find something that interests you.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";
definePageMeta({
  layout: "dashboard",
});
interface Course {
  id: number;
  title: string;
  description: string;
}

const courses = ref<Course[]>([]);

const fetchUserCourses = async () => {
  // Replace this with an actual API call
  const coursesData: Course[] = [
    {
      id: 1,
      title: "Introduction to Python",
      description: "Start your journey with Python programming from scratch.",
    },
    {
      id: 2,
      title: "HTML & CSS Essentials",
      description:
        "Learn the foundational skills to create beautiful web pages.",
    },
  ];

  courses.value = coursesData;
};

onMounted(() => {
  fetchUserCourses();
});
</script>

