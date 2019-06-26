<template>
  <div class="information flex pl-12 pb-16">
    <img :src="picto" alt>
    <p v-html="msg"></p>
  </div>
</template>

<script>
export default {
  name: "Information",
  props: {
    msg: String,
    picto: String
  }
};
</script>

<style scoped>
p {
  font-weight: 600;
  font-size: 25px;
  line-height: 38px;
  letter-spacing: 0.894844px;
  text-align: left;
  z-index: 3;
}

img {
  position: relative;
  left: 20px;
  width: 80px;
}
</style>
