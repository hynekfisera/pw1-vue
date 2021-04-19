<template>
  <div class="datetime">
    <input type="date" v-model="date" />
    <input type="time" v-model="time" />
  </div>
  <p>Hodnota: {{ date }} {{ time }}</p>
</template>

<script>
export default {
  name: "DateTimePicker",
  data() {
    return {
      date: new Date(0).toLocaleDateString("cs-CZ"),
      time: new Date(0).toLocaleTimeString("cs-CZ"),
    };
  },
};
</script>

<style scoped>
.datetime {
  display: flex;
  flex-direction: row;
}

.datetime input {
  padding: 0.5rem;
  font-size: 18px;
  border-radius: 0.5rem;
  border: 1px solid black;
  outline: none;
  margin-right: 0.5rem;
}

p {
  margin-top: 0.5rem;
}
</style>
