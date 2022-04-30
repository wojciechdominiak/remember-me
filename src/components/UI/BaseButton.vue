<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['mode'],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #5c2590;
  border: 1px solid #5c2590;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #460b6e;
  border-color: #460b6e;
}

.flat {
  background-color: transparent;
  color: #5c2590;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
