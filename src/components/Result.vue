<template>
  <div class="result flex justify-center px-20 py-24" id="result">
    <Regime
      title="prix moyen de vos <br> dépenses actuelles"
      :somme="data.repasActuel"
      :eau="data.eauActuel"
      :proteine="data.proteineActuel"
      orientation="left"
    ></Regime>
    <Regime
      title="prix moyen selon les <br> recommandations"
      :somme="data.repasNorme"
      :eau="data.eauNorme"
      :proteine="data.proteineNorme"
      orientation="middle"
    ></Regime>
    <Regime
      title="prix moyen de deux <br> repas veggie"
      :somme="data.repas2Vege"
      :eau="data.eau2Vege"
      :proteine="data.proteine2Vege"
      orientation="right"
    ></Regime>

    <div class="button bot">
      <i class="fab fa-facebook-messenger"></i>
    </div>
    <div class="button share">
      <i class="fas fa-share-alt"></i>
    </div>

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
.button {
  height: 86px;
  width: 86px;
  border-radius: 50px;
  background-color: #fff;
}

.bot {
  position: absolute;
  right: 40px;
  bottom: 150px;
}
.share {
  position: absolute;
  right: 40px;
  bottom: 40px;
}

i {
  font-size: 3rem;
  position: relative;
  left: 20px;
  top: 20px;
  color: #211987;
}

@media only screen and (max-width: 731px) {
  .result {
    flex-direction: column;
  }

  .py-24 {
    padding-left: 15px;
    padding-right: 15px;
  }
}
</style>
