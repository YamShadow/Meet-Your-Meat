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

  .px-20 {
    padding-top: 3rem;
    padding-bottom: 3rem;
  }
}
</style>
