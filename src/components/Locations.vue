<template>
  <tr>
    <th>Locations</th>
    <td v-for="observation in observations">
      {{observation.location}}
    </td>
  </tr>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations'],
};

</script>
