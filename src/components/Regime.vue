<template>
  <div class="regime text-center" :class="orientation">
    <h1 class="pb-10" v-html="title"></h1>
    <div class="info">
      <h2 class="py-16">{{ Math.round(somme)+' €' }}</h2>
      <Information :msg="stringSomme()" picto="/img/euro.png"></Information>
      <Information :msg="stringEau()" picto="/img/Water.png"></Information>
      <Information :msg="stringProteine()" picto="/img/Meat.png"></Information>
    </div>
  </div>
</template>

<script>
import Information from "@/components/Information.vue";

export default {
  name: "Regime",
  components: {
    Information
  },
  props: {
    title: String,
    somme: String,
    eau: String,
    proteine: String,
    orientation: String
  },
  methods: {
    stringSomme() {
      if (this.orientation == "left") {
        return (
          "<span style='font-weight: 900;font-size: 40px;line-height: 61px;'>" +
          Math.round(this.somme * 52) +
          " €</span><br>à l’année"
        );
      } else {
        return (
          "<span style='font-weight: 900;font-size: 40px;line-height: 61px;'>1</span> semaine à la mer <br> par an (soit " +
          Math.round(this.somme * 52) +
          " €)"
        );
      }
    },
    stringEau() {
      return (
        "<span style='font-weight: 900;font-size: 40px;line-height: 61px;'>" +
        this.eau +
        " L</span><br>d’eau consommé"
      );
    },
    stringProteine() {
      return (
        "<span style='font-weight: 900;font-size: 40px;line-height: 61px;'> " +
        this.proteine +
        "g</span><br>de protéines en trop"
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.info {
  background-color: #fff;
  width: 421px;
  color: #211987;
}

h1 {
  font-weight: 600;
  font-size: 23px;
  line-height: 35px;
  text-align: center;
  letter-spacing: 0.894844px;
  color: white;
}

h2 {
  font-family: Londrina Solid;
  font-style: normal;
  font-weight: normal;
  font-size: 70px;
  line-height: 83px;
  text-align: center;
  letter-spacing: 0.894844px;
  text-transform: uppercase;

  color: #211987;
}

.data {
  font-weight: 900;
  font-size: 40px;
  line-height: 61px;
}

.left {
  position: relative;
  left: 50px;
}
.middle {
  z-index: 2;
}
.middle h1 {
  color: #ffdd02;
  position: relative;
  top: -25px;
}

.middle .info {
  height: 750px;
  position: relative;
  top: -25px;
  border-top: 10px solid #ffdd02;
  -webkit-box-shadow: 0px 0px 43px -10px rgba(0, 0, 0, 0.74);
  -moz-box-shadow: 0px 0px 43px -10px rgba(0, 0, 0, 0.74);
  box-shadow: 0px 0px 43px -10px rgba(0, 0, 0, 0.74);
}

.right {
  position: relative;
  left: -50px;
}
</style>
