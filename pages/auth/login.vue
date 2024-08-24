<template>
  <h1 class="text-3xl font-bold mb-6 text-center">Login</h1>
  <form @submit.prevent="handleLogin" class="">
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
      Login
    </button>
    <div class="mt-4 text-center flex flex-col gap-y-4">
      <NuxtLink to="/auth/recover" class="text-blue-600 hover:text-blue-800"
        >Forgot password?</NuxtLink
      >
      <NuxtLink to="/auth/register" class="text-blue-600 hover:text-blue-800"
        >haven`t an account? Register</NuxtLink
      >
    </div>
  </form>
</template>

<script setup lang="ts">
import { ref } from "vue";
definePageMeta({
  layout: "auth",
});

const email = ref("");
const password = ref("");

function handleLogin() {
  // Handle login logic
  console.log("Login with", email.value, password.value);
}
</script>
