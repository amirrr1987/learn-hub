<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div v-if="instructor">
        <!-- Instructor Information -->
        <div class="flex items-center mb-8">
          <img
            :src="instructor.photoUrl"
            alt="Instructor Photo"
            class="w-32 h-32 rounded-full object-cover mr-6"
          />
          <div>
            <h1 class="text-3xl font-bold mb-2">{{ instructor.name }}</h1>
            <p class="text-lg text-gray-700 mb-4">{{ instructor.bio }}</p>
            <p class="text-gray-600 mb-2">
              <strong>Email:</strong>
              <a
                :href="'mailto:' + instructor.email"
                class="text-blue-600 hover:underline"
                >{{ instructor.email }}</a
              >
            </p>
            <p class="text-gray-600 mb-2">
              <strong>Website:</strong>
              <a
                :href="instructor.website"
                target="_blank"
                class="text-blue-600 hover:underline"
                >{{ instructor.website }}</a
              >
            </p>
          </div>
        </div>

        <!-- Courses Taught -->
        <div>
          <h2 class="text-2xl font-semibold mb-6">Courses Taught</h2>
          <div v-if="courses.length">
            <ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
              <li
                v-for="course in courses"
                :key="course.id"
                class="border rounded shadow-lg p-6"
              >
                <h3 class="text-xl font-semibold mb-4">{{ course.title }}</h3>
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
            <p>No courses found for this instructor.</p>
          </div>
        </div>
      </div>
      <div v-else>
        <p>Loading instructor details...</p>
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

interface Instructor {
  id: number;
  name: string;
  bio: string;
  email: string;
  website: string;
  photoUrl: string;
}

const route = useRoute();
const instructor = ref<Instructor | null>(null);
const courses = ref<Course[]>([]);

const fetchInstructorDetails = async (instructorId: number) => {
  // Replace this with an actual API call
  const instructorData: Instructor = {
    id: instructorId,
    name: "John Doe",
    bio: "John Doe is a seasoned instructor with over 10 years of experience in web development. He specializes in JavaScript frameworks and has a passion for teaching and mentoring.",
    email: "john.doe@example.com",
    website: "https://johndoe.com",
    photoUrl: "https://www.example.com/path/to/instructor-photo.jpg",
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
      title: "Advanced JavaScript",
      description:
        "Explore advanced JavaScript concepts and improve your coding skills.",
    },
  ];

  instructor.value = instructorData;
  courses.value = coursesData;
};

onMounted(() => {
  const instructorId = parseInt(route.params.id as string, 10);
  fetchInstructorDetails(instructorId);
});
</script>
