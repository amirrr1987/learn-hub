<template>
  <h1 class="text-3xl font-bold mb-6 text-center">Password Recovery</h1>
  <form @submit.prevent="handleRecovery" class="">
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
    <button
      type="submit"
      class="w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700 transition"
    >
      Send Recovery Email
    </button>
    <div class="mt-4 text-center">
      <router-link to="/auth/login" class="text-blue-600 hover:text-blue-800"
        >Remembered your password? Login</router-link
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

function handleRecovery() {
  // Handle password recovery logic
  console.log("Send recovery email to", email.value);
}
</script>
