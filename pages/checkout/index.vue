<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Checkout</h1>
        <p class="text-lg text-gray-700">
          Complete your purchase by reviewing your cart and providing payment
          details.
        </p>
      </div>

      <!-- Checkout Form -->
      <form @submit.prevent="submitOrder" class="space-y-8">
        <!-- Shipping Information -->
        <div class="bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Shipping Information</h2>
          <div class="space-y-4">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700"
                >Full Name</label
              >
              <input
                type="text"
                id="name"
                v-model="shippingInfo.name"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your full name"
              />
            </div>
            <div>
              <label
                for="address"
                class="block text-sm font-medium text-gray-700"
                >Address</label
              >
              <input
                type="text"
                id="address"
                v-model="shippingInfo.address"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your address"
              />
            </div>
            <div>
              <label for="city" class="block text-sm font-medium text-gray-700"
                >City</label
              >
              <input
                type="text"
                id="city"
                v-model="shippingInfo.city"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your city"
              />
            </div>
            <div>
              <label for="zip" class="block text-sm font-medium text-gray-700"
                >ZIP Code</label
              >
              <input
                type="text"
                id="zip"
                v-model="shippingInfo.zip"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your ZIP code"
              />
            </div>
            <div>
              <label
                for="country"
                class="block text-sm font-medium text-gray-700"
                >Country</label
              >
              <input
                type="text"
                id="country"
                v-model="shippingInfo.country"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your country"
              />
            </div>
          </div>
        </div>

        <!-- Payment Information -->
        <div class="bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Payment Information</h2>
          <div class="space-y-4">
            <div>
              <label
                for="card-number"
                class="block text-sm font-medium text-gray-700"
                >Card Number</label
              >
              <input
                type="text"
                id="card-number"
                v-model="paymentInfo.cardNumber"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your card number"
              />
            </div>
            <div>
              <label
                for="expiry-date"
                class="block text-sm font-medium text-gray-700"
                >Expiry Date</label
              >
              <input
                type="text"
                id="expiry-date"
                v-model="paymentInfo.expiryDate"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="MM/YY"
              />
            </div>
            <div>
              <label for="cvv" class="block text-sm font-medium text-gray-700"
                >CVV</label
              >
              <input
                type="text"
                id="cvv"
                v-model="paymentInfo.cvv"
                class="mt-1 block w-full px-3 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm"
                placeholder="Enter your CVV"
              />
            </div>
          </div>
        </div>

        <!-- Order Summary -->
        <div class="mt-8 bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-2xl font-semibold mb-4">Order Summary</h2>
          <div v-if="cartItems.length">
            <ul class="space-y-4">
              <li
                v-for="item in cartItems"
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
          <div v-else>
            <p>Your cart is empty.</p>
          </div>
        </div>

        <!-- Submit Button -->
        <div class="text-center mt-8">
          <button
            type="submit"
            class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition"
          >
            Complete Purchase
          </button>
        </div>
      </form>
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
}

interface ShippingInfo {
  name: string;
  address: string;
  city: string;
  zip: string;
  country: string;
}

interface PaymentInfo {
  cardNumber: string;
  expiryDate: string;
  cvv: string;
}

const cartItems = ref<CartItem[]>([
  { id: 1, name: "Course A", price: 99.99, quantity: 1 },
  { id: 2, name: "Course B", price: 149.99, quantity: 2 },
]);

const shippingInfo = ref<ShippingInfo>({
  name: "",
  address: "",
  city: "",
  zip: "",
  country: "",
});

const paymentInfo = ref<PaymentInfo>({
  cardNumber: "",
  expiryDate: "",
  cvv: "",
});

const subtotal = computed(() => {
  return cartItems.value.reduce(
    (acc, item) => acc + item.price * item.quantity,
    0
  );
});

const tax = computed(() => {
  return subtotal.value * 0.05; // 5% tax
});

const submitOrder = () => {
  // Validate form data and handle order submission
  console.log("Shipping Info:", shippingInfo.value);
  console.log("Payment Info:", paymentInfo.value);
  console.log("Cart Items:", cartItems.value);

  // Here you would typically make an API call to process the order
};
</script>
