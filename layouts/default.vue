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
  <header class="flex justify-between">
    <div class="h-8 flex items-center gap-3">
      <img src="/public/img/logo/win512pts.png" alt="Logo" class="max-h-full" />
      <h1 class="text-xl">MQ3T</h1>
    </div>
    <button-github />
  </header>
  <div class="default">
    <slot />
  </div>
  <footer>
    <div class="h-8 flex items-center gap-3">
      <img src="/public/img/logo/win512pts.png" alt="Logo" class="max-h-full" />
      <h1 class="text-xl">MQ3T</h1>
    </div>
    <button-github class="mt-4 max-w-8" />
    <p class="text-sm text-black dark:text-neutral-500">
      Copyright © {{ currentYear }} MQ3T. All rights reserved.
    </p>
  </footer>
</template>

<style scoped>
header {
  @apply absolute top-0 left-0 right-0 w-full mx-auto p-4 2xl:max-w-[1000px] 3xl:max-w-[1200px];
}

footer {
  @apply bg-black/5 dark:bg-neutral-900/20 flex flex-col items-center gap-4 mx-auto p-4 text-center;
}
</style>

<style>
body {
  font-family: "Rubik", sans-serif;

  @apply dark:bg-neutral-950 dark:text-white overflow-x-hidden max-w-[100vw];
}

::-webkit-scrollbar {
  @apply w-2;
}

::-webkit-scrollbar-track {
  @apply bg-neutral-200 dark:bg-neutral-800;
}

/* Handle */
::-webkit-scrollbar-thumb {
  @apply bg-neutral-400 transition-colors dark:bg-neutral-700 dark:transition-colors;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  @apply bg-neutral-500 dark:bg-neutral-600;
}
</style>
