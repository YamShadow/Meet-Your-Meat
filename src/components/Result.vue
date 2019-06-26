<template>
  <div class="result flex justify-center mx-10" id="result">
    <Regime msg="Carnivore"></Regime>
    <Regime msg="Norme"></Regime>
    <Regime msg="2 végé"></Regime>

    <!-- <p>Somme repas carnivore</p>
    <p>{{ data.repasActuel.toFixed(2) }}</p>
    <p>Somme repas 2 legume</p>
    <p>{{ data.repas2Vege.toFixed(2) }}</p>
    <p>Somme repas norme</p>
    <p>{{ data.repasNorme.toFixed(2) }}</p>
    <div>
      <h2>Actuel / Norme</h2>
      <div>
        <p>Economie 1 semaine</p>
        <p>{{ (data.repasActuel - data.repasNorme).toFixed(2) }}</p>
      </div>
      <div>
        <p>Economie 1 mois</p>
        <p>{{ ((data.repasActuel - data.repasNorme) * 4.33).toFixed(2) }}</p>
      </div>
      <div>
        <p>Economie 1 ans</p>
        <p>{{ ((data.repasActuel - data.repasNorme) * 52).toFixed(2) }}</p>
      </div>
    </div>

    <div>
      <h2>Actuel / 2 végé</h2>
      <div>
        <p>Economie 1 semaine</p>
        <p>{{ (data.repasActuel - data.repas2Vege).toFixed(2) }}</p>
      </div>
      <div>
        <p>Economie 1 mois</p>
        <p>{{ ((data.repasActuel - data.repas2Vege) * 4.33 ).toFixed(2)}}</p>
      </div>
      <div>
        <p>Economie 1 ans</p>
        <p>{{ ((data.repasActuel - data.repas2Vege) * 52).toFixed(2) }}</p>
      </div>
    </div>-->
  </div>
</template>

<script>
import Regime from "@/components/Regime.vue";

export default {
  name: "Result",
  components: {
    Regime
  },
  props: {
    data: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.result {
  background-color: #211987;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
