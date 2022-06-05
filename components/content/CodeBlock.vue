<script setup lang="ts">
  defineProps({
    /**
     * Label to display for the tab.
     */
    label: {
      type: String,
      required: true,
    },
    /**
     * Select which tab should be active by passing `active="true"`
     */
    active: {
      type: Boolean,
      default: false,
    },
    /**
     * Preview blocks are bordered with smaller padding.
     */
    preview: {
      type: Boolean,
      default: false,
    },
  })
</script>

<template>
  <div
    class="code-block"
    :class="{
      active,
      'rounded-lg border-2 border-t-0 border-gray-100 p-0 dark:border-gray-800': preview,
    }"
  >
    <div class="overflow-hidden max-w-screen p-4 m-0">
      <slot />
    </div>
  </div>
</template>

<style scoped>
  .code-block {
    display: none;
  }

  .code-block.active {
    display: block;
  }

  :global(:is(.code-block, pre) > :is(div code, code)) {
    overflow-x: scroll;
    max-width: 100%;
    padding: 1rem;
  }
</style>
