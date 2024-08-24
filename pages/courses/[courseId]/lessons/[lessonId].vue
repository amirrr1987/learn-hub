<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <div v-if="lesson">
        <h1 class="text-3xl font-bold mb-6">{{ lesson.title }}</h1>

        <div class="mb-8">
          <video
            v-if="lesson.videoUrl"
            controls
            class="w-full rounded shadow-lg"
          >
            <source :src="lesson.videoUrl" type="video/mp4" />
            Your browser does not support the video tag.
          </video>
          <p v-else>{{ lesson.content }}</p>
        </div>

        <div v-if="lesson.resources.length" class="mt-8">
          <h2 class="text-2xl font-semibold mb-4">Supplementary Materials</h2>
          <ul class="list-disc list-inside space-y-2">
            <li v-for="(resource, index) in lesson.resources" :key="index">
              <a
                :href="resource.url"
                target="_blank"
                class="text-blue-600 hover:underline"
              >
                {{ resource.title }}
              </a>
            </li>
          </ul>
        </div>
      </div>
      <div v-else>
        <p>Loading lesson details...</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

interface Resource {
  title: string;
  url: string;
}

interface Lesson {
  id: number;
  title: string;
  content: string;
  videoUrl?: string;
  resources: Resource[];
}

const route = useRoute();
const lesson = ref<Lesson | null>(null);

const fetchLessonDetails = async (courseId: number, lessonId: number) => {
  // Replace this with an actual API call
  const lessonData: Lesson = {
    id: lessonId,
    title: "Introduction to Vue.js",
    content:
      "This lesson covers the basics of Vue.js, including how to set up a project and build your first component.",
    videoUrl: "https://www.example.com/path/to/lesson-video.mp4",
    resources: [
      { title: "Vue.js Documentation", url: "https://vuejs.org/v2/guide/" },
      {
        title: "Component Basics",
        url: "https://vuejs.org/v2/guide/components.html",
      },
    ],
  };

  lesson.value = lessonData;
};

onMounted(() => {
  const courseId = parseInt(route.params.courseId as string, 10);
  const lessonId = parseInt(route.params.lessonId as string, 10);
  fetchLessonDetails(courseId, lessonId);
});
</script>
