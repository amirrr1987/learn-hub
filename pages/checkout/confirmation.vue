<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Order Confirmation</h1>
        <p class="text-lg text-gray-700">
          Thank you for your purchase! Your order has been successfully
          processed.
        </p>
      </div>

      <!-- Order Summary -->
      <div class="bg-white border rounded-lg shadow-lg p-6 mb-8">
        <h2 class="text-2xl font-semibold mb-4">Order Summary</h2>
        <div v-if="order">
          <div class="mb-4">
            <h3 class="text-xl font-semibold">Order ID: {{ order.id }}</h3>
            <p class="text-gray-600">Date: {{ order.date }}</p>
          </div>

          <div class="space-y-4">
            <ul class="space-y-4">
              <li
                v-for="item in order.items"
                :key="item.id"
                class="flex justify-between"
              >
                <span>{{ item.name }} ({{ item.quantity }})</span>
                <span>$ {{ (item.price * item.quantity).toFixed(2) }}</span>
              </li>
            </ul>
            <div class="flex justify-between mt-4">
              <span class="text-lg font-semibold">Subtotal:</span>
              <span class="text-lg font-semibold"
                >$ {{ subtotal.toFixed(2) }}</span
              >
            </div>
            <div class="flex justify-between mt-4">
              <span class="text-lg font-semibold">Tax (5%):</span>
              <span class="text-lg font-semibold">$ {{ tax.toFixed(2) }}</span>
            </div>
            <div class="flex justify-between mt-4">
              <span class="text-lg font-semibold">Total:</span>
              <span class="text-lg font-semibold"
                >$ {{ (subtotal + tax).toFixed(2) }}</span
              >
            </div>
          </div>
        </div>
        <div v-else>
          <p>No order details available.</p>
        </div>
      </div>

      <!-- Additional Information -->
      <div class="text-center">
        <p class="text-lg mb-4">
          You will receive a confirmation email with your order details shortly.
        </p>
        <router-link
          to="/"
          class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition"
        >
          Return to Home
        </router-link>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

interface OrderItem {
  id: number;
  name: string;
  price: number;
  quantity: number;
}

interface Order {
  id: string;
  date: string;
  items: OrderItem[];
}

const order = ref<Order | null>(null);

// Mock data for demonstration purposes
order.value = {
  id: "123456789",
  date: "2024-08-24",
  items: [
    { id: 1, name: "Course A", price: 99.99, quantity: 1 },
    { id: 2, name: "Course B", price: 149.99, quantity: 2 },
  ],
};

const subtotal = computed(() => {
  return (
    order.value?.items.reduce(
      (acc, item) => acc + item.price * item.quantity,
      0
    ) ?? 0
  );
});

const tax = computed(() => {
  return subtotal.value * 0.05; // 5% tax
});
</script>

<style scoped>
.container {
  max-width: 800px;
}

h1,
h2,
h3 {
  margin-bottom: 16px;
}

button {
  cursor: pointer;
}

.border {
  border-width: 1px;
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

.text-gray-600 {
  color: #4b5563; /* Tailwind's gray-600 */
}

.text-blue-600 {
  color: #2563eb; /* Tailwind's blue-600 */
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

.rounded-lg {
  border-radius: 0.5rem; /* Tailwind's rounded-lg */
}

.shadow-lg {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Tailwind's shadow-lg */
}

.mt-8,
.mt-4 {
  margin-top: 2rem; /* Tailwind's mt-8 and mt-4 */
}

.hover\:bg-blue-700:hover {
  background-color: #1d4ed8; /* Tailwind's blue-700 */
}

.transition {
  transition: background-color 0.3s ease;
}
</style>
