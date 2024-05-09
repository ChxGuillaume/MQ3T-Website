<script setup lang="ts">
import { usePreferredColorScheme } from "@vueuse/core";
import DownloadButton from "~/components/DownloadButton.vue";

useHead({ title: "MQ3T" });

const preferredColor = usePreferredColorScheme();
const img = useImage();

const imageModifiers = { width: 1400, height: 904 };
const placeHolderModifiers = {
  modifiers: {
    width: Math.round(1400 / 3),
    height: Math.round(904 / 3),
    blur: 3,
    q: 30,
  },
};

const images = {
  light: img(`/img/mq3t-light.png`, imageModifiers),
  dark: img(`/img/mq3t-dark.png`, imageModifiers),
};

const placeholders = {
  light: img.getSizes(`/img/mq3t-light.png`, placeHolderModifiers),
  dark: img.getSizes(`/img/mq3t-dark.png`, placeHolderModifiers),
};
</script>

<template>
  <div>
    <div class="radial-wrapper">
      <div class="radial-bg"></div>
    </div>
    <div
      class="tw-w-min-h-lvh tw-flex tw-justify-center tw-items-center tw-flex-col"
    >
      <div
        class="tw-mt-20 xl:tw-mt-52 2xl:tw-mt-64 tw-mb-16 2xl:tw-mb-24 tw-flex tw-flex-col tw-items-center tw-gap-8 tw-text-center"
      >
        <h1 class="tw-text-4xl">
          The last MQTT development tool you'll ever need
        </h1>
        <download-button />
      </div>
      <q-img
        :ratio="1400 / 904"
        :src="images[preferredColor]"
        :placeholder-src="placeholders[preferredColor]?.src"
        alt="MQ3T"
        class="app-image"
      />
    </div>
  </div>
</template>

<style scoped>
.app-image {
  @apply xl:tw-w-[1100px] 3xl:tw-w-[1400px] tw-max-w-full;
}

.radial-wrapper {
  @apply tw-absolute tw-top-0 tw-left-0 tw-w-full -tw-z-50 tw-overflow-hidden;
}

.radial-wrapper .radial-bg {
  @apply tw-relative tw-bg-primary tw-w-[200vw] xl:tw-w-full tw-h-[1000px] tw-left-[-50%] xl:tw-left-0 tw-right-[-50%] xl:tw-right-0;

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
