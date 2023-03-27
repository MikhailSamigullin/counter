<template>
  <div v-for="n in countersNumber" :key="n">
    <CounterComponent />
  </div>
  <AddCounterComponent @click="addNewCounter" />
</template>

<script>
import CounterComponent from "./components/CounterComponent.vue";
import AddCounterComponent from "./components/AddCounterComponent.vue";

export default {
  name: "App",
  data() {
    return {
      countersNumber: 1,
    };
  },
  methods: {
    addNewCounter() {
      this.countersNumber += 1;
    },
  },
  components: {
    CounterComponent,
    AddCounterComponent,
  },
};
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
}

#app {
  font-family: "Gotham Pro", sans-serif;
  font-weight: 400;
  font-size: 22px;
  padding: 50px 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
  color: #2c3e50;
  background-color: #353638;
}
</style>
