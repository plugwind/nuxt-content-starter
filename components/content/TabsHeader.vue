<script setup lang="ts">
import { nextTick, ref, watch } from 'vue'
import type { PropType } from 'vue'

const props = defineProps({
  tabs: {
    type: Array as PropType<{ label: string }[]>,
    required: true,
  },
  activeTabIndex: {
    type: Number,
    required: true,
  },
})

const emit = defineEmits(['update:activeTabIndex'])

const tabsRef = ref()

const highlightUnderline = ref()

function updateHighlightUnderlinePosition() {
  const activeTab = tabsRef.value[props.activeTabIndex]

  if (!activeTab) return

  highlightUnderline.value.style.left = `${activeTab.offsetLeft}px`
  highlightUnderline.value.style.top = `${activeTab.offsetTop}px`
  highlightUnderline.value.style.width = `${activeTab.clientWidth}px`
  highlightUnderline.value.style.height = `${activeTab.clientHeight}px`
  highlightUnderline.value.style.transform = `scale(1)`
  highlightUnderline.value.style.opacity = 1
}

function updateTabs(i) {
  emit('update:activeTabIndex', i)
  nextTick(() => updateHighlightUnderlinePosition())
}

watch(
  tabsRef,
  (newVal) => {
    if (!newVal) return

    setTimeout(() => {
      updateHighlightUnderlinePosition()
    }, 50)
  },
  {
    immediate: true,
  },
)
</script>

<template>
  <div class="tabs-header relative text-white bg-stone-700">
    <div v-if="tabs" class="relative z-0 px-2">
      <button
        v-for="({ label }, i) in tabs"
        ref="tabsRef"
        :key="`${i}${label}`"
        class="text-white xs:py-3 xs:my-0 relative text-sm my-2 rounded-md px-2 pt-1.5 pb-1 font-display focus:outline-none z-10"
        :class="[activeTabIndex === i ? 'text-white' : '!text-gray-300 hover:text-gray-100 duration-300 transition-base transition-colors']"
        @click="updateTabs(i)"
      >
        {{ label }}
      </button>
      <span
        ref="highlightUnderline"
        class="highlight-underline xs:py-1.5 absolute z-[-1]"
        :style="{
          transform: `scale(1)`,
          opacity: 1,
        }"
      >
        <span class="flex h-full w-full rounded bg-gray-600" />
      </span>
    </div>

    <slot name="footer" />
  </div>
</template>

<style lang="postcss" scoped>
  .highlight-underline {
    /* bottom: -2px; */
    /* height: 2px; */
    transition: left 150ms, top 150ms, width 150ms, height 150ms, transform 100ms, opacity 100ms;
  }
</style>
