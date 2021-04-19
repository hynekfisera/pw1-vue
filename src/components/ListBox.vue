<template>
  <div class="select">
    <span :class="{ selected: moznost.key == selectedKey }" @click="select(moznost.key)" value="moznost.key" :key="moznost.key" v-for="moznost in moznosti">{{ moznost.nazev }}</span>
  </div>
  <p>Hodnota: {{ selectedKey }}</p>
</template>

<script>
export default {
  name: "ListBox",
  data() {
    return {
      moznosti: [],
      selectedKey: "moznost1",
    };
  },
  methods: {
    select(key) {
      this.selectedKey = key;
    },
  },
  created() {
    this.moznosti = [
      {
        nazev: "Možnost 1",
        key: "moznost1",
      },
      {
        nazev: "Možnost 2",
        key: "moznost2",
      },
      {
        nazev: "Možnost 3",
        key: "moznost3",
      },
      {
        nazev: "Možnost 4",
        key: "moznost4",
      },
      {
        nazev: "Možnost 5",
        key: "moznost5",
      },
    ];
  },
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  border: 1px solid black;
}

span {
  padding: 0.75rem;
  font-size: 18px;
  outline: none;
  background-color: #f5f5f5;
}

span:hover {
  background-color: #eee;
}

.selected {
  background-color: #ddd;
}

span:not(:last-child) {
  border-bottom: 1px solid black;
}

p {
  margin-top: 0.5rem;
}
</style>
