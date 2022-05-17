<template>
  <TheHeader :title="title" />
  <TheResources></TheResources>
</template>

<script setup>
import TheResources from './components/learning-resources/TheResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';

const title = 'Remember Me!';
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
