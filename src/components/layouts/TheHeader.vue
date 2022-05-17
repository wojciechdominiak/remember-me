<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script setup>
/* eslint-disable no-unused-vars */
import { defineProps } from "vue";
  const props = defineProps( {
    title: String,
  });
</script>

<style scoped>
header {
  height: 6rem;
  background-color: #5c2590;
  display: flex;
  justify-content: center;
  align-items: center;
}

header h1 {
  color: white;
}
</style>

