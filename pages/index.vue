<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <!-- Hero Section -->
      <div class="text-center mb-12">
        <h1 class="text-4xl font-bold mb-4">Welcome to LearnHub</h1>
        <p class="text-lg text-gray-700 mb-6">
          Discover and master new skills with our diverse range of online
          courses.
        </p>
        <router-link
          to="/courses"
          class="inline-block px-6 py-3 bg-blue-600 text-white rounded hover:bg-blue-700 transition"
        >
          Explore Courses
        </router-link>
      </div>

      <!-- Featured Courses -->
      <div class="mb-12">
        <h2 class="text-3xl font-bold mb-6">Featured Courses</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="course in featuredCourses"
            :key="course.id"
            class="border rounded shadow-lg p-6"
          >
            <h3 class="text-xl font-semibold mb-4">{{ course.title }}</h3>
            <p class="text-gray-600 mb-4">{{ course.description }}</p>
            <router-link
              :to="`/courses/${course.id}`"
              class="text-blue-600 hover:underline"
            >
              Learn More
            </router-link>
          </div>
        </div>
      </div>
      <!-- Call to Action -->
      <div class="text-center mt-12">
        <h2 class="text-2xl font-semibold mb-4">Ready to get started?</h2>
        <router-link
          to="/auth/register"
          class="inline-block px-6 py-3 bg-green-600 text-white rounded hover:bg-green-700 transition"
        >
          Sign Up Now
        </router-link>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

interface Course {
  id: number;
  title: string;
  description: string;
}

const featuredCourses = ref<Course[]>([]);

const fetchFeaturedCourses = async () => {
  // Replace this with an actual API call
  const coursesData: Course[] = [
    {
      id: 1,
      title: "Vue.js for Beginners",
      description:
        "An introductory course to Vue.js, perfect for getting started with modern web development.",
    },
    {
      id: 2,
      title: "Advanced React",
      description:
        "Deep dive into advanced React concepts and patterns to enhance your React applications.",
    },
    {
      id: 3,
      title: "Full-Stack JavaScript",
      description:
        "Learn to build both frontend and backend applications using JavaScript and modern frameworks.",
    },
  ];

  featuredCourses.value = coursesData;
};

onMounted(() => {
  fetchFeaturedCourses();
});
</script>

<style scoped>
.container {
  max-width: 1200px;
}

h1,
h2,
h3 {
  margin-bottom: 16px;
}

button,
a {
  cursor: pointer;
}

.text-center {
  text-align: center;
}

.grid {
  display: grid;
  gap: 2rem;
}

.border {
  border-width: 1px;
  border-color: #e5e7eb; /* Tailwind's gray-200 */
}
</style>
