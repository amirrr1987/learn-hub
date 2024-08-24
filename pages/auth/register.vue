<template>
  <h1 class="text-3xl font-bold mb-6 text-center">Register</h1>
  <form @submit.prevent="handleRegister" class="">
    <div class="mb-4">
      <label for="name" class="block text-gray-700 mb-2">Name</label>
      <input
        id="name"
        type="text"
        v-model="name"
        class="w-full px-4 py-2 border rounded-md"
        placeholder="Enter your name"
        required
      />
    </div>
    <div class="mb-4">
      <label for="email" class="block text-gray-700 mb-2">Email</label>
      <input
        id="email"
        type="email"
        v-model="email"
        class="w-full px-4 py-2 border rounded-md"
        placeholder="Enter your email"
        required
      />
    </div>
    <div class="mb-6">
      <label for="password" class="block text-gray-700 mb-2">Password</label>
      <input
        id="password"
        type="password"
        v-model="password"
        class="w-full px-4 py-2 border rounded-md"
        placeholder="Enter your password"
        required
      />
    </div>
    <button
      type="submit"
      class="w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700 transition"
    >
      Register
    </button>
    <div class="mt-4 text-center">
      <NuxtLink to="/auth/login" class="text-blue-600 hover:text-blue-800"
        >Already have an account? Login</NuxtLink
      >
    </div>
  </form>
</template>

<script setup lang="ts">
import { ref } from "vue";
definePageMeta({
  layout: "auth",
});
const name = ref("");
const email = ref("");
const password = ref("");

function handleRegister() {
  // Handle register logic
  console.log("Register with", name.value, email.value, password.value);
}
</script>
