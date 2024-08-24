<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Account Settings</h1>
        <p class="text-lg text-gray-700">
          Update your account information and manage your settings here.
        </p>
      </div>

      <!-- Settings Form -->
      <form @submit.prevent="updateSettings" class="space-y-8">
        <!-- Profile Information -->
        <div class="bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Profile Information</h2>
          <div class="space-y-4">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700"
                >Name</label
              >
              <input
                type="text"
                id="name"
                v-model="form.name"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your name"
              />
            </div>
            <div>
              <label for="email" class="block text-sm font-medium text-gray-700"
                >Email</label
              >
              <input
                type="email"
                id="email"
                v-model="form.email"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your email"
              />
            </div>
          </div>
        </div>

        <!-- Password Change -->
        <div class="bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Change Password</h2>
          <div class="space-y-4">
            <div>
              <label
                for="current-password"
                class="block text-sm font-medium text-gray-700"
                >Current Password</label
              >
              <input
                type="password"
                id="current-password"
                v-model="form.currentPassword"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your current password"
              />
            </div>
            <div>
              <label
                for="new-password"
                class="block text-sm font-medium text-gray-700"
                >New Password</label
              >
              <input
                type="password"
                id="new-password"
                v-model="form.newPassword"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your new password"
              />
            </div>
            <div>
              <label
                for="confirm-password"
                class="block text-sm font-medium text-gray-700"
                >Confirm New Password</label
              >
              <input
                type="password"
                id="confirm-password"
                v-model="form.confirmPassword"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Confirm your new password"
              />
            </div>
          </div>
        </div>

        <!-- Save Button -->
        <div class="text-center">
          <button
            type="submit"
            class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition"
          >
            Save Changes
          </button>
        </div>
      </form>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
definePageMeta({
  layout: "dashboard",
});
interface SettingsForm {
  name: string;
  email: string;
  currentPassword: string;
  newPassword: string;
  confirmPassword: string;
}

const form = ref<SettingsForm>({
  name: "",
  email: "",
  currentPassword: "",
  newPassword: "",
  confirmPassword: "",
});

const updateSettings = () => {
  // Validate form data and handle settings update
  if (form.value.newPassword !== form.value.confirmPassword) {
    alert("New passwords do not match");
    return;
  }

  // Here you would typically make an API call to update settings
  console.log("Settings updated:", form.value);
};
</script>

<style scoped>
.container {
  max-width: 800px;
}

h1,
h2 {
  margin-bottom: 16px;
}

input {
  border-color: #e5e7eb; /* Tailwind's gray-200 */
}

.bg-white {
  background-color: #ffffff; /* Tailwind's white */
}

.bg-blue-600 {
  background-color: #2563eb; /* Tailwind's blue-600 */
}

.text-gray-700 {
  color: #374151; /* Tailwind's gray-700 */
}

.text-gray-500 {
  color: #6b7280; /* Tailwind's gray-500 */
}

.hover\:bg-blue-700:hover {
  background-color: #1d4ed8; /* Tailwind's blue-700 */
}

.transition {
  transition: background-color 0.3s ease;
}

.border {
  border-width: 1px;
  border-color: #e5e7eb; /* Tailwind's gray-200 */
}

.rounded-lg {
  border-radius: 0.5rem; /* Tailwind's rounded-lg */
}

.shadow-lg {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Tailwind's shadow-lg */
}

.px-4,
.py-12 {
  padding: 1rem; /* Tailwind's px-4 and py-12 */
}
</style>
