<template>
  <tr>
    <th>Locations</th>
    <td class="location"
      v-for="observation in observations">
      {{observation.location}}
    </td>
  </tr>
</template>

<script type = "text/javascript" >

export default {
  props: ['observations'],
};

</script>
