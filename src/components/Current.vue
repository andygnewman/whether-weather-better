<template>
  <tr>
    <th>Now</th>
    <td v-for="observation in observations">
      {{observation.current.temp}}
    </td>
  </tr>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations'],
};

</script>
