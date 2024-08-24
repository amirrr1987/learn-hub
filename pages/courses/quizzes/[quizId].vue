<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div v-if="quiz">
        <h1 class="text-3xl font-bold mb-6">{{ quiz.title }}</h1>
        <form @submit.prevent="submitQuiz">
          <div v-for="(question, index) in quiz.questions" :key="index" class="mb-8">
            <h2 class="text-xl font-semibold mb-4">{{ index + 1 }}. {{ question.text }}</h2>
            <div v-for="(option, optIndex) in question.options" :key="optIndex" class="mb-2">
              <label class="flex items-center">
                <input type="radio" :name="'question-' + index" :value="option" v-model="userAnswers[index]" class="mr-2" />
                {{ option }}
              </label>
            </div>
          </div>
          <button type="submit" class="px-6 py-3 bg-blue-600 text-white rounded hover:bg-blue-700 transition">
            Submit Quiz
          </button>
        </form>
      </div>
      <div v-else>
        <p>Loading quiz...</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

interface Question {
  text: string;
  options: string[];
}

interface Quiz {
  id: number;
  title: string;
  questions: Question[];
}

const route = useRoute();
const quiz = ref<Quiz | null>(null);
const userAnswers = ref<string[]>([]);

const fetchQuizDetails = async (courseId: number, quizId: number) => {
  // Replace this with an actual API call
  const quizData: Quiz = {
    id: quizId,
    title: 'Vue.js Basics Quiz',
    questions: [
      { text: 'What is Vue.js?', options: ['A JavaScript framework', 'A CSS framework', 'A database'] },
      { text: 'Which directive is used to bind data in Vue?', options: ['v-bind', 'v-for', 'v-if'] },
      { text: 'What is a Vue component?', options: ['A reusable UI element', 'A database model', 'A CSS style'] }
    ]
  };
  
  quiz.value = quizData;
  userAnswers.value = new Array(quizData.questions.length).fill('');
};

const submitQuiz = () => {
  console.log('User answers:', userAnswers.value);
  // Here you would typically send the user's answers to an API for grading
};

onMounted(() => {
  const courseId = parseInt(route.params.courseId as string, 10);
  const quizId = parseInt(route.params.quizId as string, 10);
  fetchQuizDetails(courseId, quizId);
});
</script>

