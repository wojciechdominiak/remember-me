<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script setup>
import { defineProps } from "vue";

/* eslint-disable no-unused-vars */
  const props = defineProps( {
    title: String,
  });
</script>

<style scoped>
header {
  height: 6rem;
  background-color: #5c2590;
  display: grid;
  place-items:  center;
}

header h1 {
  color: white;
}
</style>

