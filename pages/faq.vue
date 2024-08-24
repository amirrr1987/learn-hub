<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold mb-4">Frequently Asked Questions</h1>
        <p class="text-lg text-gray-700">Find answers to some of the most common questions about our courses and services.</p>
      </div>

      <!-- FAQ List -->
      <div class="space-y-8">
        <div v-for="faq in faqs" :key="faq.id" class="bg-white border rounded-lg shadow-lg p-6">
          <h2 class="text-xl font-semibold mb-4">{{ faq.question }}</h2>
          <p class="text-gray-600">{{ faq.answer }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

interface FAQ {
  id: number;
  question: string;
  answer: string;
}

const faqs = ref<FAQ[]>([
  {
    id: 1,
    question: 'What is the duration of each course?',
    answer: 'Each course varies in duration, typically ranging from 4 to 12 weeks. You can check the specific duration on the course details page.'
  },
  {
    id: 2,
    question: 'How do I access the course materials?',
    answer: 'Once enrolled, you will have access to all course materials through your dashboard. You can download resources and access videos anytime.'
  },
  {
    id: 3,
    question: 'What is your refund policy?',
    answer: 'We offer a 14-day refund policy if you are not satisfied with the course. Please refer to our refund policy page for more details.'
  },
  {
    id: 4,
    question: 'Can I interact with instructors?',
    answer: 'Yes, you can interact with instructors through the course forums and during live Q&A sessions. Detailed instructions are provided within each course.'
  }
]);
</script>

