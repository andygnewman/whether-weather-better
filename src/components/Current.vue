<template>
  <tr>
    <th>Now</th>
    <td v-for="observation in observations">
      {{(Math.round(observation.current.temp * 10 ) / 10).toFixed(1)}}
    </td>
  </tr>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations'],
};

</script>
