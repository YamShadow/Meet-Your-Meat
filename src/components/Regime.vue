<template>
  <div class="regime">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "Regime",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.regime {
  background-color: #fff;
  max-width: 421px;
  color: #211987;
}
</style>
