<script setup lang="ts">
import ButtonGithub from "~/components/ButtonGithub.vue";

const title = "MQ3T";
const description = "The last MQTT development tool you'll ever need";
const image = "/img/screenshots/topics/topics-2-mix.png";

useHead({
  htmlAttrs: { lang: "en" },
  link: [{ rel: "icon", href: "/img/logo/win512pts.ico" }],
});

const route = useRoute();

useSeoMeta({
  title,
  ogTitle: title,
  twitterTitle: title,
  description,
  ogDescription: description,
  twitterDescription: description,
  ogImage: image,
  twitterImage: image,
  twitterCard: "summary_large_image",
  ogLocale: "en_US",
  ogUrl: route.fullPath,
});

const currentYear = new Date().getFullYear();
</script>

<template>
  <header class="tw-flex tw-justify-between">
    <div class="tw-h-8 tw-flex tw-items-center tw-gap-3">
      <img
        src="/public/img/logo/win512pts.png"
        alt="Logo"
        class="tw-max-h-full"
      />
      <h1 class="tw-text-xl">MQ3T</h1>
    </div>
    <button-github />
  </header>
  <div class="default">
    <slot />
  </div>
  <footer>
    <div class="tw-h-8 tw-flex tw-items-center tw-gap-3">
      <img
        src="/public/img/logo/win512pts.png"
        alt="Logo"
        class="tw-max-h-full"
      />
      <h1 class="tw-text-xl">MQ3T</h1>
    </div>
    <button-github class="mt-4 max-w-8" />
    <p class="tw-text-sm tw-text-black dark:tw-text-neutral-500">
      Copyright © {{ currentYear }} MQ3T. All rights reserved.
    </p>
  </footer>
</template>

<style scoped>
header {
  @apply tw-absolute tw-top-0 tw-left-0 tw-right-0 tw-w-full tw-mx-auto tw-p-4 2xl:tw-max-w-[1000px] 3xl:tw-max-w-[1200px];
}

footer {
  @apply tw-bg-black/5 dark:tw-bg-neutral-900/20 tw-flex tw-flex-col tw-items-center tw-gap-4 tw-mx-auto tw-p-4 tw-text-center;
}

.default {
  @apply tw-min-h-lvh;
}
</style>

<style>
body {
  font-family: "Rubik", sans-serif;

  @apply dark:tw-bg-neutral-950 dark:tw-text-white tw-overflow-x-hidden tw-max-w-[100vw];
}

::-webkit-scrollbar {
  @apply tw-w-2;
}

::-webkit-scrollbar-track {
  @apply tw-bg-neutral-200 dark:tw-bg-neutral-800;
}

/* Handle */
::-webkit-scrollbar-thumb {
  @apply tw-bg-neutral-400 tw-transition-colors dark:tw-bg-neutral-700 dark:tw-transition-colors;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  @apply tw-bg-neutral-500 dark:tw-bg-neutral-600;
}
</style>
