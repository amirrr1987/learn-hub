<template>
  <div>
    <Navbar />
    <main>
      <nav class="py-6">
        <div class="container mx-auto px-4">
          <ul class="flex gap-x-4 justify-center">
            <NuxtLink class="text-gray" to="/dashboard/">dashboard</NuxtLink>
            <NuxtLink class="text-gray" to="/dashboard/courses">courses</NuxtLink>
            <NuxtLink class="text-gray" to="/dashboard/messages">messages</NuxtLink>
            <NuxtLink class="text-gray" to="/dashboard/progress">progress</NuxtLink>
            <NuxtLink class="text-gray" to="/dashboard/settings">settings</NuxtLink>
          </ul>
        </div>
      </nav>
      <slot />
    </main>
  </div>
</template>
