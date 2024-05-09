<script setup lang="ts">
import { usePreferredColorScheme } from "@vueuse/core";
import DownloadButton from "~/components/DownloadButton.vue";

useHead({ title: "MQ3T" });

const preferredColor = usePreferredColorScheme();
const appImage = computed(() => {
  return preferredColor.value === "light" ? "mq3t-light.png" : "mq3t-dark.png";
});
</script>

<template>
  <div>
    <div class="radial-wrapper">
      <div class="radial-bg"></div>
    </div>
    <div class="min-h-lvh flex justify-center items-center flex-col">
      <div
        class="mt-20 xl:mt-52 2xl:mt-64 mb-16 2xl:mb-24 flex flex-col items-center gap-8 text-center"
      >
        <h1 class="text-4xl">
          The last MQTT development tool you'll ever need {{ preferredColor }}
        </h1>
        <download-button />
      </div>
      <img class="app-image" :src="`_nuxt/public/img/${appImage}`" alt="MQ3T" />
    </div>
  </div>
</template>

<style scoped>
.app-image {
  @apply xl:w-[1100px] 3xl:w-[1400px] max-w-full;
}

.radial-wrapper {
  @apply absolute top-0 left-0 w-full -z-50 overflow-hidden;
}

.radial-wrapper .radial-bg {
  @apply relative bg-primary w-[200vw] xl:w-full h-[1000px] left-[-50%] xl:left-0 right-[-50%] xl:right-0;

  animation: glow 2s alternate infinite;
  mask-image: radial-gradient(rgba(0, 0, 0, 0.45), transparent 75%);
}

@keyframes glow {
  from {
    filter: brightness(0.8);
  }
  to {
    filter: brightness(1.2);
  }
}
</style>
