<template>
  <div class="py-5 sm:py-10">
    <Html lang="en" />
    <Meta property="og:image" content="/cover.jpg" />
    <Meta name="twitter:card" content="summary_large_image" />
    <Navbar />
    <NuxtPage />
  </div>
</template>

<style global lang="postcss">
  body {
    @apply bg-gray-50 text-gray-900 dark:(bg-stone-900 text-gray-50) transition-colors duration-100 linear;
  }
  .prose + :is(h1, h2, h3), 
  .prose > :is(h1, h2, h3):not(:first-child) {
    @apply mt-6;
  }
  .prose :is(h1, h2, h3) {
    @apply tracking-tight;
  }
  .prose h1 {
    @apply text-4xl font-extrabold;
  }
  .prose h2 {
    @apply text-3xl font-semibold;
  }
  .prose h3 {
    @apply text-xl font-bold;
  }
  .prose :is(h1,h2,h3) > a[href] {
    @apply no-underline ease-all border-b border-dashed border-neutral-500/50 dark:border-neutral-300/50;

    &:hover {
      @apply border-neutral-600 dark:border-neutral-300;
    }
  }

  :is(.prose, p) svg {
    @apply inline-block align-bottom;
  }

  /* monospace font for *all* code blocks */
  pre, code {
    @apply !font-mono;
  }
  
  pre {
    @apply bg-neutral-800 dark:bg-neutral-900 text-white px-0 py-0 mx-[-20px] my-4 rounded-none sm:(mx-0 rounded-md);
    @apply leading-6 tracking-tight [tab-width:2];
    overflow-x: scroll;
    overflow-y: hidden;

    & > code {
      white-space: pre-wrap;
      @apply !my-0 py-0;

      & .line {
        @apply px-6 leading-5 pt-1 pb-0.5 block;
      }
    }
  }
  
  :is(div.relative) > pre {
    @apply px-6 pt-5 pb-2;
  }

  :is(.code-block, .code-group) {
    @apply mt-2 mb-4 !pb-0;
  }


  /* inline code blocks */
  :not(pre) > code {
    @apply !text-sm bg-gray-100 text-warm-gray-900 border border-b-2 border-gray-200 dark:!text-white dark:!bg-neutral-400/30 dark:!border-neutral-600/50;
    @apply rounded px-1.5 pt-[4px] pb-0.5 mx-px;
  }

  /* fancy line numbers */
  :not(.no-numbers) > :is(pre):is(:not(.no-numbers)) {
    counter-reset: line;
    @apply px-0 py-0;

    & > code {
      @apply my-0;

      & .line {
        counter-increment: line;
        @apply bg-black/0 border-black/0 pb-px border-b-[1px] border-dashed w-full !block min-w-full;
        transition: opacity .5s ease-out, color .5s ease-out, background .5s ease-out, border-color 0.4s ease;

        &::before {
          content: counter(line);
          @apply pr-4 min-w-[1.8rem] inline-block leading-5 text-sm opacity-60;
          transition: opacity .3s ease-in;
        }
        &:hover::before {
          @apply opacity-100;
        }
      }
      &:hover {
        & .line {
          &:hover {
            @apply !opacity-100 bg-black/20 border-black cursor-default;

            &::before {
              @apply opacity-100;
            }
          }
          &:not(:hover) {
            @apply !opacity-70;
          }
        }
      }
    }
  }

  .code-group-content > div {
    @apply !px-0

    & > pre {
      @apply !my-0 !mb-0 !mx-0;
    
      & > code {
        @apply !mx-0 ;
      }
    }
  }  

  /* full-width images */
  .full-bleed img, img.full-bleed {
    @apply block w-[calc(100%-1rem)] rounded-md overflow-clip mx-auto my-4 sm:(mx-auto my-4);
    @apply ring-2 ring-offset-1 ring-offset-white dark:(ring-offset-warm-gray-900 ring-white/15) ring-stone-400/10;
  }

  .prose a[href] {
    @apply underline decoration-gray-600/40 hover:decoration-gray-600/60 transition-colors ease-in duration-400 dark:5                    
  }
</style>,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,tfeq,
