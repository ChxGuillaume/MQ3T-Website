<script setup lang="ts">
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
  <div class="default">
    <slot />
  </div>
</template>

<style scoped></style>
