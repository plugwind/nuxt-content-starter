<template>
  <div class="nuxt-content-wrapper">
    <ContentDoc class="prose prose-gray dark:prose-invert max-w-none">
      <template #not-found>
        <h1 class="text-2xl">
          Page not found
        </h1>
      </template>
    </ContentDoc>
  </div>
</template>

<style global lang="postcss">
  .nuxt-content-wrapper {
    @apply bg-white dark:bg-gray-800;
    @apply max-w-4xl px-4 py-10 m-auto sm:(px-8 rounded shadow) <sm:shadow-sm md:shadow-md;
    transition: box-shadow 0.3s ease-in, filter 0.3s ease-in, background-color 0.1s linear;
  }
</style>
