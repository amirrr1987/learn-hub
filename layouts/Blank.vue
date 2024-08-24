<template>
  <main>
    <div class="max-w-lg bg-red">
      <slot />
    </div>
  </main>
</template>
<script setup lang="ts">
definePageMeta({
  layout: "auth",
});
</script>
