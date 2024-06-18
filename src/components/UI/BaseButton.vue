<template>
  <button :type="type" :class="mode">
    <!-- we could have used a prop here but slots allow for passing icons as well -->
    <slot></slot>
  </button>
</template>

<script>
export default {
  /* Type here could also be a fall through prop (omitted)*/
  props: ['type', 'mode'],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #270041;
  border-color: #270041;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
