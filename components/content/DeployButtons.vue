<script lang="ts" setup>
  import { format } from '~/composables'
  defineProps({
    enabled: {
      type: String as Lowercase<`${'cloudflare'|'github'|'netlify'|'railway'|'render'|'vercel'}${','|''}`>,
      default: ['vercel', 'netlify'],
    },
    repository: {
      type: String,
      default: 'https://github.com/plugwind/nuxt-content-starter'
    }
  })

  const providers = ref<{ [K in keyof typeof props]: Record<string, string> }>({
    vercel: {
      button: 'https://vercel.com/button',
      deploy: 'https://vercel.com/new/clone?repository-url={0}',
      label: 'Vercel',
    },
    netlify: {
      button: 'https://www.netlify.com/img/deploy/button.svg',
      deploy: 'https://app.netlify.com/start/deploy?repository={0}',
      label: 'Netlify',
    },
    railway: {
      button: 'https://railway.app/button.svg',
      deploy: 'https://railway.app/new?template={0}',
      label: 'Railway',
    }
  })
</script>

<template>
  <Divider size="1" style="dotted"/>

  <div class="flex flex-row <sm:flex-wrap gap-x-2 gap-y-2 place-items-center justify-center w-auto mx-auto pt-0.5 !pb-0 mt-2 mb-0">
    <span v-for="[provider, data] of Object.entries(providers)">
      <a
        :href="format(data.deploy, encodeURIComponent(repository))"
        rel="nofollow noopener noreferrer"
        class="flex-shrink-0"
        target="_blank"
        :title="(`Deploy with ${data.label}`)"
        :aria-label="(`Deploy with ${data.label}`)"
        v-if="enabled!.includes(provider.toLowerCase())"
      >
        <img 
          :src="data.button"
          :alt="(`Deploy with ${data.label}`)"
          class="w-auto h-8"
          role="button"
        />
      </a>
    </span>
  </div>
  <Divider size="1" style="inset"/>

  <slot />
</template>
<style>

</style>