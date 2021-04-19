<template>
  <h1>Vue.js komponenty</h1>
  <h2>Tabulka</h2>
  <Tabulka />
  <h2>DateTimePicker</h2>
  <DateTimePicker />
  <h2>ListBox</h2>
  <ListBox />
  <h2>TreeView</h2>
  <TreeView />
</template>

<script>
import Tabulka from "./components/Tabulka.vue";
import DateTimePicker from "./components/DateTimePicker.vue";
import ListBox from "./components/ListBox.vue";
import TreeView from "./components/TreeView.vue";

export default {
  name: "App",
  components: {
    Tabulka,
    DateTimePicker,
    ListBox,
    TreeView,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Rubik", sans-serif;
  font-size: 16px;
  font-weight: 500;
}

#app {
  max-width: 400px;
  margin: 3rem auto;
}

#app h1 {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
}

#app h2 {
  font-size: 2.25rem;
  font-weight: 300;
  margin: 3rem 0 1rem;
}
</style>
