<template>
  <tbody>
    <tr v-for="(forecastDate, index) in forecastDates">
      <th>{{`${new Date(forecastDate).getDate()}/${new Date(forecastDate).getMonth()}`}}</th>
      <td v-for="observation in observations">
        {{(Math.round(observation.forecasts[index] * 10 ) / 10).toFixed(1)}}
      </td>
    </tr>
  </tbody>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations', 'forecastDates'],
};

</script>
