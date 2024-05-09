<script setup lang="ts">
import DownloadButton from "~/components/DownloadButton.vue";

useHead({ title: "MQ3T" });
</script>

<template>
  <div>
    <div class="radial-wrapper">
      <div class="radial-bg"></div>
    </div>
    <div class="min-h-dvh flex justify-center items-center flex-col">
      <h1 class="my-52 text-4xl text-center">
        The last MQTT development tool you'll ever need
      </h1>
      <download-button />
      <img
        class="app-image"
        src="/public/img/mqt3-dark.png"
        alt="App Preview"
      />
    </div>
    <div class="min-h-dvh">test</div>
  </div>
</template>

<style scoped>
.app-image {
  @apply 2xl:w-[1100px] 3xl:w-[1400px] max-w-full;
}

.radial-wrapper {
  @apply absolute top-0 left-0 w-full -z-50;
}

.radial-wrapper .radial-bg {
  @apply bg-primary relative h-[1000px] w-full;

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
