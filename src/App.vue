<template>
  <div id="app">
    <h1>Whether Weather Better</h1>
    <table>
      <locations v-bind:observations="weather.observations"></locations>
      <current v-bind:observations="weather.observations"></current>
      <future
        v-bind:observations="weather.observations"
        v-bind:forecastDates="weather.forecastDates"
      ></future>
    </table>
    <bestNow v-bind:bestNowLocation="bestNowLocation"></bestNow>
    <bestForecast v-bind:bestForecastLocation="bestForecastLocation"></bestForecast>

  </div>
</template>

<script>
  import Locations from './components/Locations';
  import Current from './components/Current';
  import Future from './components/Future';
  import BestNow from './components/BestNow';
  import BestForecast from './components/BestForecast';
  import mockData from '../test/mocks/api-data-mock.json';

  export default {
    name: 'app',
    components: {
      Locations,
      Current,
      Future,
      BestNow,
      BestForecast,
    },
    data() {
      return {
        weather: mockData.weather,
        bestNowLocation: 'Dublin',
        bestForecastLocation: 'Dublin',
        timer: null,
      };
    },
    mounted() {
      this.fetchWeatherData()
        .then(() => {
          this.whereIsBestNow();
          this.whereIsBestForecast();
          this.timer = setInterval(this.fetchWeatherData, 1000 * 60 * 30);
        });
    },
    methods: {
      fetchWeatherData() {
        return fetch('https://whether-weather-api.herokuapp.com/', { mode: 'cors' })
          .then(response => response.json())
          .then((json) => {
            this.weather = json.weather;
          });
      },
      whereIsBestNow() {
        this.bestNowLocation = this.weather.observations.slice().sort((a, b) => {
          if (a.current.temp < b.current.temp) {
            return -1;
          }
          if (a.current.temp > b.current.temp) {
            return 1;
          }
          return 0;
        }).pop().location;
      },
      whereIsBestForecast() {
        this.bestForecastLocation = this.weather.observations.slice().sort((a, b) => {
          const totalTemp = forecasts => forecasts.reduce((acc, currVal) => acc + currVal);
          if (totalTemp(a.forecasts) < totalTemp(b.forecasts)) {
            return -1;
          }
          if (totalTemp(a.forecasts) > totalTemp(b.forecasts)) {
            return 1;
          }
          return 0;
        }).pop().location;
      },
      cancelAutoUpdate() {
        clearInterval(this.timer);
      },
    },
    beforeDestroy() {
      this.cancelAutoUpdate();
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
table {
  margin: 0 auto;
}
td, th {
  border: 1px, solid, grey;
  min-width: 100px;
  padding: 0 5px;
}
.location {
  font-weight: bold;
}
</style>
