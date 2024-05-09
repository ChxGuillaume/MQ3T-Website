<script setup lang="ts">
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
</script>

<template>
  <a
    href="https://github.com/ChxGuillaume/MQ3T"
    target="_blank"
    class="tw-w-8 tw-h-8"
  >
    <font-awesome-icon icon="fab fa-github" class="icon-github" />
  </a>
</template>

<style scoped>
.icon-github {
  @apply tw-w-full tw-h-full tw-text-black dark:tw-text-white tw-transition-colors;
}

.icon-github:hover {
  @apply tw-text-gray-700 dark:tw-text-neutral-300;
}
</style>
