<template>
  <div>
    <h2>Where's Expected To Be Best</h2>
    <p>{{bestForecastLocation}} has the highest average forecast midday temperature across the next five days</p>
  </div>
</template>

<script type = "text/javascript" >

export default {
  props: ['bestForecastLocation'],
};

</script>
