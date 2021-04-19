<template>
  <div class="radek">
    <div>
      <td :key="sloupec.id" v-for="sloupec in sloupce">{{ radek[sloupec.key] }}</td>
    </div>
    <div class="buttons">
      <IconButton @click="$emit('zmenit-radek', radek.id)" icon="edit" color="blue" />
      <IconButton @click="$emit('smazat-radek', radek.id)" icon="trash" color="red" />
    </div>
  </div>
</template>

<script>
import IconButton from "./IconButton";

export default {
  name: "Radek",
  props: {
    radek: Object,
    sloupce: Array,
  },
  components: {
    IconButton,
  },
};
</script>

<style scoped>
.radek {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  background-color: #f5f5f5;
  padding: 0.75rem;
  margin-bottom: 0.5rem;
}

.radek td {
  font-size: 1.5rem;
  font-weight: 500;
  display: inline-block;
  margin-right: 0.5rem;
}

.buttons {
  display: flex;
  flex-direction: row;
}

.buttons button {
  margin-left: 0.25rem;
}
</style>
