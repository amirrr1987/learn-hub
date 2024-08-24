<template>
  <main class="h-screen flex justify-center items-center bg-gray-50">
    <section
      class="w-full max-w-lg bg-white shadow border border-solid border-gray-50 p-4 rounded"
    >
      <NuxtLink to="/" class="block w-max mx-auto mb-4">
        <img class="rounded-full" src="https://placehold.co/200x200" title="logo" alt="logo" />
      </NuxtLink>
      <slot />
    </section>
  </main>
</template>
