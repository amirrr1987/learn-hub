<template>
  <nav class="bg-gray-800 p-4">
    <div class="container mx-auto flex justify-between items-center">
      <!-- Logo or Brand Name -->
      <div class="text-white text-2xl font-bold">
        <router-link to="/">MyLearning</router-link>
      </div>

      <!-- Navbar Links -->
      <div class="hidden md:flex space-x-4">
        <router-link
          to="/"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Home</router-link
        >
        <router-link
          to="/courses"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Courses</router-link
        >
        <router-link
          to="/categories"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Categories</router-link
        >
        <router-link
          to="/instructors"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Instructors</router-link
        >
        <router-link
          to="/dashboard"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Dashboard</router-link
        >
        <router-link
          to="/search"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Search</router-link
        >
        <router-link
          to="/contact"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Contact</router-link
        >
        <router-link
          to="/about"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >About</router-link
        >
        <router-link
          to="/faq"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >FAQ</router-link
        >
        <router-link
          to="/auth/login"
          class="text-white hover:bg-gray-700 px-3 py-2 rounded"
          >Login</router-link
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
      <router-link to="/" class="block px-4 py-2">Home</router-link>
      <router-link to="/courses" class="block px-4 py-2">Courses</router-link>
      <router-link to="/categories" class="block px-4 py-2"
        >Categories</router-link
      >
      <router-link to="/instructors" class="block px-4 py-2"
        >Instructors</router-link
      >
      <router-link to="/dashboard" class="block px-4 py-2"
        >Dashboard</router-link
      >
      <router-link to="/search" class="block px-4 py-2">Search</router-link>
      <router-link to="/contact" class="block px-4 py-2">Contact</router-link>
      <router-link to="/about" class="block px-4 py-2">About</router-link>
      <router-link to="/faq" class="block px-4 py-2">FAQ</router-link>
      <router-link to="/login" class="block px-4 py-2">Login</router-link>
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
