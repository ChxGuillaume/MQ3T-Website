<script setup lang="ts">
interface APIBody {
  email: string;
}

const { data } = useFetch<APIBody>(
  "https://guillaumechx.dev/mq3t-contact-informations.php",
  {
    lazy: true,
    server: false,
  },
);
</script>

<template>
  <div
    class="tw-min-h-svh tw-flex tw-justify-center tw-items-center tw-flex-col tw-gap-2"
  >
    <h1 class="tw-text-2xl">Contact:</h1>
    <ul>
      <li>
        <a
          class="text-xl hover:tw-underline"
          href="https://github.com/ChxGuillaume/MQ3T/issues"
        >
          Github Issues
        </a>
      </li>
      <li>{{ data?.email }}</li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  @apply tw-flex tw-flex-col tw-gap-2;
}

ul li {
  @apply tw-text-center;
}
</style>
