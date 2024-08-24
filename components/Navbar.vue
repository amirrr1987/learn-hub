<template>
  <nav class="bg-gray-800 p-4">
    <div class="container mx-auto flex justify-between items-center">
      <!-- Logo or Brand Name -->
      <div class="text-white text-2xl font-bold">
        <NuxtLink to="/">MyLearning</NuxtLink>
      </div>

      <!-- Navbar Links -->
      <div class="hidden md:flex space-x-4">
        <NuxtLink to="/" class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Home</NuxtLink
        >
        <NuxtLink
          to="/courses"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Courses</NuxtLink
        >
        <NuxtLink
          to="/categories"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Categories</NuxtLink
        >
        <NuxtLink
          to="/instructors"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Instructors</NuxtLink
        >
        <NuxtLink
          to="/dashboard"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Dashboard</NuxtLink
        >
        <NuxtLink
          to="/search"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Search</NuxtLink
        >
        <NuxtLink
          to="/contact"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Contact</NuxtLink
        >
        <NuxtLink
          to="/about"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >About</NuxtLink
        >
        <NuxtLink
          to="/faq"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >FAQ</NuxtLink
        >
        <NuxtLink
          to="/auth/login"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Login</NuxtLink
        >
      </div>

      <!-- Mobile Menu Button -->
      <div class="md:hidden flex items-center">
        <button @click="toggleMenu" class="text-white focus:outline-none">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div v-show="isMenuOpen" class="md:hidden bg-gray-800 text-white py-2">
      <NuxtLink to="/" class="block px-4 py-2">Home</NuxtLink>
      <NuxtLink to="/courses" class="block px-4 py-2">Courses</NuxtLink>
      <NuxtLink to="/categories" class="block px-4 py-2">Categories</NuxtLink>
      <NuxtLink to="/instructors" class="block px-4 py-2">Instructors</NuxtLink>
      <NuxtLink to="/dashboard" class="block px-4 py-2">Dashboard</NuxtLink>
      <NuxtLink to="/search" class="block px-4 py-2">Search</NuxtLink>
      <NuxtLink to="/contact" class="block px-4 py-2">Contact</NuxtLink>
      <NuxtLink to="/about" class="block px-4 py-2">About</NuxtLink>
      <NuxtLink to="/faq" class="block px-4 py-2">FAQ</NuxtLink>
      <NuxtLink to="/login" class="block px-4 py-2">Login</NuxtLink>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref } from "vue";

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>
