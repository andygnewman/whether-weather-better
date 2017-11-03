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

export default {
  name: 'app',
  components: {
    Locations,
    Current,
    Future,
  },
  data() {
    return {
      observations: [
        {
          location: 'Dublin',
          current: {
            temp: 18,
          },
          forecasts: [17, 19, 20, 22, 12],
        },
      ],
      forecastDates: ['4/11', '5/11', '6/11', '7/11', '8/11'],
    };
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
