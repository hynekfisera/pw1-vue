<template>
  <button :style="{ background: color }"><i :class="['fas fa-' + icon]"></i></button>
</template>

<script>
export default {
  name: "IconButton",
  props: {
    icon: String,
    color: String,
  },
};
</script>

<style scoped>
button {
  padding: 0.5rem;
  color: white;
  border: none;
  outline: none;
  border-radius: 0.25rem;
}
</style>
