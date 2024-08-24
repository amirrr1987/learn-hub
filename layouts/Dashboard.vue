<template>
  <div>
    <Navbar />
    <main>
      <nav>
        <ul>
          <NuxtLink to="/dashboard/">dashboard</NuxtLink>
          <NuxtLink to="/dashboard/courses">courses</NuxtLink>
          <NuxtLink to="/dashboard/messages">messages</NuxtLink>
          <NuxtLink to="/dashboard/progress">progress</NuxtLink>
          <NuxtLink to="/dashboard/settings">settings</NuxtLink>
        </ul>
      </nav>
      <slot />
    </main>
  </div>
</template>
