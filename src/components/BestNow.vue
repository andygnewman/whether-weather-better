<template>
  <div>
    <h2>Where's Best Right Now</h2>
    <p>It is currently warmest in {{bestNowLocation}}</p>
  </div>
</template>

<script type = "text/javascript" >

export default {
  props: ['bestNowLocation'],
};

</script>
