<script setup lang="ts">
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
</script>

<template>
  <a
    href="https://github.com/ChxGuillaume/MQ3T"
    target="_blank"
    class="w-8 h-8"
  >
    <font-awesome-icon icon="fab fa-github" class="icon-github" />
  </a>
</template>

<style scoped>
.icon-github {
  @apply w-full h-full text-black dark:text-white transition-colors;
}

.icon-github:hover {
  @apply text-gray-700 dark:text-neutral-300;
}
</style>
