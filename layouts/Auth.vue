<template>
  <main class="h-screen flex justify-center items-center bg-gray-50">
    <section
      class="w-full max-w-lg bg-white shadow border border-solid border-gray-50 p-4 rounded"
    >
      <NuxtLink to="/">
        <img src="https://placehold.co/400x400" title="logo" alt="logo" />
      </NuxtLink>
      <slot />
    </section>
  </main>
</template>
