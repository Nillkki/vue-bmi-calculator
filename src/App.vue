<template>
  <div id="app">
    <h1>BMI Calculator</h1>
    <label for="weight">Weight</label>
    <input type="number" id="weight" v-model.lazy="weight" :placeholder="'Enter weight in kg'">
    <label for="height">Height</label>
    <input type="number" id="height" v-model.lazy="height" :placeholder="'Enter height in cm'">
    <button v-on:click="calculateBmi" :disabled='!isFilled'>Calculate</button>
    <p> Your BMI is {{ bmi }} </p>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class App extends Vue {
  weight = 0

  height = 0

  bmi = 0

  calculateBmi() {
    this.bmi = (this.weight / ((this.height / 100) ** 2)).toFixed(2);
  }

  // Declared as computed property getter
  get isFilled() {
    return this.weight && this.height;
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
