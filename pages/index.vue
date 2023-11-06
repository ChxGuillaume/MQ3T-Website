<script setup lang="ts">
useHead({ title: "MQ3T" });

const counter = ref(0);
</script>

<template>
  <div class="bg-red-400">
    <h1>Index</h1>
    <p>Counter: {{ counter }}</p>
    <button @click="counter++">Increment</button>
  </div>
</template>

<style scoped></style>
