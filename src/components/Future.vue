<template>
  <tbody>
    <tr v-for="(forecastDate, index) in forecastDates">
      <th>{{forecastDate}}</th>
      <td v-for="observation in observations">
        {{observation.forecasts[index]}}
      </td>
    </tr>
  </tbody>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations', 'forecastDates'],
};

</script>
