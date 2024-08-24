<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">User Dashboard</h1>
        <p class="text-lg text-gray-700">
          Welcome back, {{ user?.name }}! Here's an overview of your recent
          activity and enrolled courses.
        </p>
      </div>

      <!-- User Information -->
      <div class="mb-12 border rounded-lg shadow-lg p-6">
        <h2 class="text-2xl font-semibold mb-4">Profile Information</h2>
        <div class="flex items-center mb-4">
          <img
            :src="user?.photoUrl"
            alt="User Photo"
            class="w-24 h-24 rounded-full object-cover mr-6"
          />
          <div>
            <p class="text-xl font-bold mb-2">{{ user?.name }}</p>
            <p class="text-gray-600 mb-2">
              <strong>Email:</strong> {{ user?.email }}
            </p>
            <p class="text-gray-600">
              <strong>Joined:</strong> {{ user?.joinedDate }}
            </p>
          </div>
        </div>
      </div>

      <!-- Enrolled Courses -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold mb-6">Enrolled Courses</h2>
        <div v-if="enrolledCourses.length">
          <ul
            class="list-none grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8"
          >
            <li
              v-for="course in enrolledCourses"
              :key="course.id"
              class="border rounded-lg shadow-lg p-6"
            >
              <h3 class="text-xl font-semibold mb-4">{{ course?.title }}</h3>
              <p class="text-gray-600 mb-4">{{ course?.description }}</p>
              <NuxtLink
                :to="`/courses/${course.id}`"
                class="text-blue-600 hover:underline"
              >
                Continue Learning
              </NuxtLink>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>
            You are not enrolled in any courses yet. Browse our
            <NuxtLink to="/courses" class="text-blue-600 hover:underline"
              >course catalog</NuxtLink
            >
            to find something interesting.
          </p>
        </div>
      </div>

      <!-- Recent Activity -->
      <div>
        <h2 class="text-2xl font-semibold mb-6">Recent Activity</h2>
        <div v-if="recentActivity.length">
          <ul class="list-disc pl-5">
            <li
              v-for="activity in recentActivity"
              :key="activity.id"
              class="mb-4"
            >
              <p class="text-gray-700">{{ activity.message }}</p>
              <p class="text-sm text-gray-500">{{ activity.date }}</p>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>No recent activity to show.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
definePageMeta({
  layout: "dashboard",
});
interface Course {
  id: number;
  title: string;
  description: string;
}

interface Activity {
  id: number;
  message: string;
  date: string;
}

interface User {
  name: string;
  email: string;
  joinedDate: string;
  photoUrl: string;
}

const user = ref<User | null>(null);
const enrolledCourses = ref<Course[]>([]);
const recentActivity = ref<Activity[]>([]);

const fetchUserData = async () => {
  // Replace this with an actual API call
  const userData: User = {
    name: "Jane Doe",
    email: "jane.doe@example.com",
    joinedDate: "January 15, 2022",
    photoUrl: "https://placehold.co/96x96",
  };

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

  const activityData: Activity[] = [
    {
      id: 1,
      message: 'Completed the "Introduction to Python" course.',
      date: "August 23, 2024",
    },
    {
      id: 2,
      message: 'Started the "HTML & CSS Essentials" course.',
      date: "August 20, 2024",
    },
  ];

  user.value = userData;
  enrolledCourses.value = coursesData;
  recentActivity.value = activityData;
};

onMounted(() => {
  fetchUserData();
});
</script>
