<script setup lang="ts">
  defineProps({
    lang: {
      type: String as typeof import('shiki').Lang,
      required: false,
    }
  })
</script>

<template>
  <div class="relative">
    <pre :class="lang ? `language-${lang}` : ''"><Markdown :use="$slots.default" unwrap="p" /></pre>
  </div>
</template>
