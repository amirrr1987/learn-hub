<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Your Cart</h1>
        <p class="text-lg text-gray-700">
          Review the items in your cart before proceeding to checkout.
        </p>
      </div>

      <!-- Cart Items -->
      <div v-if="cartItems.length">
        <ul class="space-y-6">
          <li
            v-for="item in cartItems"
            :key="item.id"
            class="border rounded-lg shadow-lg p-6 bg-white flex items-center justify-between"
          >
            <div class="flex items-center space-x-4">
              <img
                :src="item.image"
                alt="Item Image"
                class="w-24 h-24 object-cover rounded-lg"
              />
              <div>
                <h2 class="text-xl font-semibold mb-2">{{ item.name }}</h2>
                <p class="text-gray-600 mb-2">
                  Price: ${{ item.price.toFixed(2) }}
                </p>
                <p class="text-gray-600">Quantity: {{ item.quantity }}</p>
              </div>
            </div>
            <div class="text-right">
              <p class="text-lg font-semibold">
                Total: ${{ (item.price * item.quantity).toFixed(2) }}
              </p>
              <button
                @click="removeItem(item.id)"
                class="mt-4 px-4 py-2 bg-red-600 text-white rounded hover:bg-red-700 transition"
              >
                Remove
              </button>
            </div>
          </li>
        </ul>

        <!-- Cart Summary -->
        <div class="mt-8 bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Cart Summary</h2>
          <div class="flex justify-between mb-4">
            <span class="text-lg font-semibold">Subtotal:</span>
            <span class="text-lg font-semibold"
              >$ {{ subtotal.toFixed(2) }}</span
            >
          </div>
          <div class="flex justify-between mb-4">
            <span class="text-lg font-semibold">Tax (5%):</span>
            <span class="text-lg font-semibold">$ {{ tax.toFixed(2) }}</span>
          </div>
          <div class="flex justify-between mb-4">
            <span class="text-lg font-semibold">Total:</span>
            <span class="text-lg font-semibold"
              >$ {{ (subtotal + tax).toFixed(2) }}</span
            >
          </div>
          <div class="text-center mt-6">
            <router-link
              to="/checkout"
              class="px-6 py-3 bg-blue-600 text-white rounded hover:bg-blue-700 transition"
            >
              Proceed to Checkout
            </router-link>
          </div>
        </div>
      </div>
      <div v-else>
        <p>Your cart is empty. Add some items to your cart to see them here.</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

interface CartItem {
  id: number;
  name: string;
  price: number;
  quantity: number;
  image: string;
}

const cartItems = ref<CartItem[]>([
  {
    id: 1,
    name: "Course A",
    price: 99.99,
    quantity: 1,
    image: "https://placehold.co/150",
  },
  {
    id: 2,
    name: "Course B",
    price: 149.99,
    quantity: 2,
    image: "https://placehold.co/150",
  },
]);

const subtotal = computed(() => {
  return cartItems.value.reduce(
    (acc, item) => acc + item.price * item.quantity,
    0
  );
});

const tax = computed(() => {
  return subtotal.value * 0.05; // 5% tax
});

const removeItem = (id: number) => {
  cartItems.value = cartItems.value.filter((item) => item.id !== id);
};
</script>
