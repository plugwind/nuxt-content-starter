<template>
  <div class="flex justify-between max-w-4xl px-4 py-4 mx-auto sm:px-8">
    <!-- Navigation -->
    <div class="text-gray-700 dark:text-gray-200">
      <ContentNavigation v-slot="{ navigation }">
        <NuxtLink
          v-for="link of navigation"
          :key="link._path"
          :to="link._path"
          active-class="font-bold"
          class="mr-4"
        >
          {{ link.navTitle || link.title }}
        </NuxtLink>
      </ContentNavigation>
    </div>
    <div class="space-x-5 text-gray-500 transition-colors duration-300 ease-in">
      <!-- ColorModeSwitch -->
      <ColorModeSwitch
        class="hover:text-yellow-500 dark:hover:text-blue-200 transition-colors duration-400 ease-in"
      />

      <!-- Twitter Icon -->
      <a
        class="hover:text-sky-400 dark:hover:text-sky-500 duration-400 ease-colors"
        href="https://twitter.com/nberlette"
        title="Twitter"
      >
        <Icon name="tabler:brand-twitter" />
      </a>

      <!-- GitHub Icon -->
      <a
        class="hover:text-gray-800 dark:hover:text-gray-300 transition-colors duration-300 ease-in"
        href="https://github.com/nberlette/content-wind"
        title="GitHub" 
      >
        <Icon name="tabler:brand-github" />
      </a>
    </div>
  </div>
</template>

<style scoped lang="postcss">
  
</style>