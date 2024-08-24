<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div v-if="category">
        <h1 class="text-3xl font-bold mb-6">{{ category.name }}</h1>
        <p class="text-gray-700 mb-8">{{ category.description }}</p>

        <div v-if="courses.length">
          <ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <li
              v-for="course in courses"
              :key="course.id"
              class="border rounded shadow-lg p-6"
            >
              <h2 class="text-xl font-semibold mb-4">{{ course.title }}</h2>
              <p class="text-gray-600 mb-4">{{ course.description }}</p>
              <router-link
                :to="`/courses/${course.id}`"
                class="text-blue-600 hover:underline"
              >
                View Course
              </router-link>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>No courses available in this category.</p>
        </div>
      </div>
      <div v-else>
        <p>Loading category details...</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

interface Course {
  id: number;
  title: string;
  description: string;
}

interface Category {
  id: number;
  name: string;
  description: string;
}

const route = useRoute();
const category = ref<Category | null>(null);
const courses = ref<Course[]>([]);

const fetchCategoryDetails = async (categoryId: number) => {
  // Replace this with an actual API call
  const categoryData: Category = {
    id: categoryId,
    name: "Web Development",
    description:
      "Courses that teach the essentials of web development, from frontend to backend.",
  };
  const coursesData: Course[] = [
    {
      id: 1,
      title: "Vue.js for Beginners",
      description:
        "Learn the basics of Vue.js and build your first web application.",
    },
    {
      id: 2,
      title: "Advanced React",
      description:
        "Take your React skills to the next level with advanced concepts and techniques.",
    },
    {
      id: 3,
      title: "Full-Stack JavaScript",
      description:
        "Master both frontend and backend development with JavaScript.",
    },
  ];

  category.value = categoryData;
  courses.value = coursesData;
};

onMounted(() => {
  const categoryId = parseInt(route.params.categoryId as string, 10);
  fetchCategoryDetails(categoryId);
});
</script>

<style scoped>
.container {
  max-width: 1000px;
}

h1,
h2 {
  margin-bottom: 16px;
}

.grid {
  display: grid;
  gap: 2rem;
}

li {
  list-style-type: none;
}

.border {
  border-width: 1px;
  border-color: #e5e7eb; /* Tailwind's gray-200 */
}
</style>
