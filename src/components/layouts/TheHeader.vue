<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
header {
  height: 5rem;
  background-color: #5c2590;
  display: flex;
  justify-content: center;
  align-items: center;
}

header h1 {
  color: white;
}
</style>

