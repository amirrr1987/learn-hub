<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Messages</h1>
        <p class="text-lg text-gray-700">
          Check your messages and notifications here. Stay updated with
          important information.
        </p>
      </div>

      <!-- Messages List -->
      <div>
        <div v-if="messages.length">
          <ul class="list-none space-y-4">
            <li
              v-for="message in messages"
              :key="message.id"
              class="border rounded-lg shadow-lg p-6 bg-white"
            >
              <h2 class="text-xl font-semibold mb-2">{{ message.title }}</h2>
              <p class="text-gray-600 mb-4">{{ message.body }}</p>
              <p class="text-sm text-gray-500">{{ message.date }}</p>
              <button
                @click="markAsRead(message.id)"
                class="mt-4 px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition"
              >
                Mark as Read
              </button>
            </li>
          </ul>
        </div>
        <div v-else>
          <p>
            No messages to display. Check back later for updates or
            notifications.
          </p>
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
interface Message {
  id: number;
  title: string;
  body: string;
  date: string;
  read: boolean;
}

const messages = ref<Message[]>([]);

const fetchMessages = async () => {
  // Replace this with an actual API call
  const messagesData: Message[] = [
    {
      id: 1,
      title: "Course Update",
      body: 'Your course "Introduction to Python" has been updated with new content.',
      date: "August 23, 2024",
      read: false,
    },
    {
      id: 2,
      title: "New Course Available",
      body: 'A new course on "Advanced JavaScript" is now available. Check it out!',
      date: "August 20, 2024",
      read: false,
    },
  ];

  messages.value = messagesData;
};

const markAsRead = (messageId: number) => {
  const message = messages.value.find((msg) => msg.id === messageId);
  if (message) {
    message.read = true;
  }
};

onMounted(() => {
  fetchMessages();
});
</script>

