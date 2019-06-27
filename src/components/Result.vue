<template>
  <div class="result flex justify-center px-20 py-24" id="result">
    <Regime
      title="prix moyen de vos <br> dépenses actuelles"
      :somme="data.repasActuel"
      :eau="data.eauActuel"
      :proteine="data.proteineActuel"
      economie="0"
      orientation="left"
    ></Regime>
    <Regime
      title="prix moyen selon les <br> recommandations"
      :somme="data.repasNorme"
      :eau="data.eauNorme"
      :proteine="data.proteineNorme"
      :economie="data.repasActuel - data.repasNorme"
      orientation="middle"
    ></Regime>
    <Regime
      title="prix moyen de deux <br> repas veggie"
      :somme="data.repas2Vege"
      :eau="data.eau2Vege"
      :proteine="data.proteine2Vege"
      :economie="data.repasActuel - data.repas2Vege"
      orientation="right"
    ></Regime>

    <div class="button bot">
      <a target="_blank" href="https://www.facebook.com/messages/t/823013504748806">
        <img src="../assets/bot.png" alt>
        <div class="notif">1</div>
      </a>
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
  position: fixed;
  right: 40px;
  bottom: 150px;
}
.share {
  position: fixed;
  right: 40px;
  bottom: 40px;
  border: 2px solid #211987;
}

i {
  font-size: 3rem;
  position: relative;
  left: 17px;
  top: 17px;
  color: #211987;
}

.notif {
  background-color: red;
  width: 25px;
  height: 25px;
  text-align: center;
  color: #fff;
  border-radius: 50%;
  position: relative;
  top: -90px;
  font-weight: 600;
  font-size: 15px;
  line-height: 29px;
  letter-spacing: 0.894844px;
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
