<template>
  <div id="app">
    <h1>Whether Weather Better</h1>
    <table>
      <locations v-bind:observations="observations"></locations>
      <current v-bind:observations="observations"></current>
      <future
        v-bind:observations="observations"
        v-bind:forecastDates="forecastDates"
      ></future>
    </table>
  </div>
</template>

<script>
import Locations from './components/Locations';
import Current from './components/Current';
import Future from './components/Future';
import mockData from '../test/mocks/api-data-mock.json';

export default {
  name: 'app',
  components: {
    Locations,
    Current,
    Future,
  },
  data() {
    return mockData;
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
