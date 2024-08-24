<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Search Results</h1>
        <p class="text-lg text-gray-700">Showing results for "{{ query }}"</p>
      </div>

      <!-- Results List -->
      <div v-if="results.length > 0" class="space-y-8">
        <div
          v-for="result in results"
          :key="result.id"
          class="bg-white border rounded-lg shadow-lg p-6"
        >
          <h2 class="text-xl font-semibold mb-4">{{ result.title }}</h2>
          <p class="text-gray-600 mb-4">{{ result.description }}</p>
          <router-link
            :to="result.link"
            class="text-blue-600 hover:text-blue-700 transition"
          >
            Read More
          </router-link>
        </div>
      </div>
      <div v-else class="text-center">
        <p class="text-lg text-gray-600">
          No results found. Try searching with different keywords.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useRoute } from "vue-router";

interface SearchResult {
  id: number;
  title: string;
  description: string;
  link: string;
}

const route = useRoute();
const query = (route.query.q as string) || "";

const results = ref<SearchResult[]>([
  {
    id: 1,
    title: "Introduction to Vue.js",
    description:
      "Learn the basics of Vue.js, a popular JavaScript framework for building user interfaces.",
    link: "/courses/1",
  },
  {
    id: 2,
    title: "Advanced Vue.js Techniques",
    description:
      "Dive deeper into Vue.js with advanced concepts and techniques to enhance your applications.",
    link: "/courses/2",
  },
  // Add more mock data or fetch from an API based on the query
]);
</script>

<style scoped>
.container {
  max-width: 800px;
}

h1,
h2 {
  margin-bottom: 16px;
}

.bg-white {
  background-color: #ffffff; /* Tailwind's white */
}

.border {
  border-width: 1px;
  border-color: #e5e7eb; /* Tailwind's gray-200 */
}

.shadow-lg {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Tailwind's shadow-lg */
}

.rounded-lg {
  border-radius: 0.5rem; /* Tailwind's rounded-lg */
}

.text-gray-700 {
  color: #374151; /* Tailwind's gray-700 */
}

.text-gray-600 {
  color: #4b5563; /* Tailwind's gray-600 */
}

.text-blue-600 {
  color: #2563eb; /* Tailwind's blue-600 */
}

.text-blue-700 {
  color: #1d4ed8; /* Tailwind's blue-700 */
}

.text-lg {
  font-size: 1.125rem; /* Tailwind's text-lg */
}

.text-xl {
  font-size: 1.25rem; /* Tailwind's text-xl */
}

.font-semibold {
  font-weight: 600; /* Tailwind's font-semibold */
}

.mt-4 {
  margin-top: 1rem; /* Tailwind's mt-4 */
}

.space-y-8 > * + * {
  margin-top: 2rem; /* Tailwind's space-y-8 */
}

.hover\:text-blue-700:hover {
  color: #1d4ed8; /* Tailwind's blue-700 */
}

.transition {
  transition: color 0.3s ease;
}
</style>
