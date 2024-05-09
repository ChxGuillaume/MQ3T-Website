<script setup lang="ts">
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

const title = "MQ3T";

const description =
  "MQTT Tools - A simple MQTT client for your development needs";
const image = "/img/screenshots/topics-mix.png";

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
</script>

<template>
  <header class="flex justify-between">
    <div class="h-8 flex items-center gap-3">
      <img src="/public/img/logo/win512pts.png" alt="Logo" class="max-h-full" />
      <h1 class="text-xl">MQ3T</h1>
    </div>
    <a
      href="https://github.com/ChxGuillaume/MQ3T"
      target="_blank"
      class="w-8 h-8"
    >
      <font-awesome-icon icon="fab fa-github" class="icon-github" />
    </a>
  </header>
  <div class="default">
    <slot />
  </div>
</template>

<style scoped>
header {
  @apply mx-auto p-4 2xl:max-w-[1000px] 3xl:max-w-[1200px];
}

.icon-github {
  @apply w-full h-full text-black dark:text-white transition-colors;
}

.icon-github:hover {
  @apply text-gray-700 dark:text-neutral-300;
}
</style>

<style>
body {
  font-family: "Rubik", sans-serif;

  @apply dark:bg-neutral-950 dark:text-white;
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
