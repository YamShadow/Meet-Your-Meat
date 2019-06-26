<template>
  <div>
    <div class="home px-40 py-10">
      <Menu></Menu>
      <div class="questionnaire mt-32">
        <form action="post" @submit="send">
          <p>
            Vous êtes
            <!-- <input type="number" min="0" v-model="nbUsers" name="nbUsers" id="nbUsers"> personnes dans le foyer -->
            <select v-model.number="nbUsers" name="nbUsers" id="nbUsers">
              <option v-for="n in 10" :key="n+'users'">{{ n }}</option>
            </select> personnes dans le foyer
          </p>
          <p>
            dont
            <select v-model.number="nbChildren" name="nbChildren" id="nbChildren">
              <option>0</option>
              <option v-for="n in nbUsers" :key="n+'children'">{{ n }}</option>
            </select> enfant.
          </p>
          <p>
            Vous avez mangé
            <select
              v-model.number="nbRepasCarne"
              name="nbRepasCarne"
              id="nbRepasCarne"
            >
              <option>0</option>
              <option v-for="n in 14" :key="n+'repas'">{{ n }}</option>
            </select> fois de la viande ou du poisson
            <br>dans la semaine.
          </p>
          <button>Eco'nomise</button>
        </form>
      </div>
    </div>

    <div v-if="dataResult.display">
      <Result :data="dataResult"></Result>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Menu from "@/components/Menu.vue";
import Result from "@/components/Result.vue";

export default {
  name: "home",
  components: {
    Menu,
    Result
  },
  data() {
    return {
      nbUsers: 0,
      nbEat: 14,
      nbChildren: 0,
      nbRepasCarne: 0,
      repasCarneAnnuel: 4646.15,
      repasVegetarienAnnuel: 3469.37,
      partChildren: 0.6,
      dataResult: {
        display: false,
        repasActuel: 0,
        repasNorme: 0,
        repas2Vege: 0
      }
    };
  },
  updated: () => {
    scroll();
    window.scrollTo({
      behavior: "smooth",
      left: 0,
      top: document.getElementById("app").scrollHeight
    });
  },
  methods: {
    send(e) {
      e.preventDefault();
      this.dataResult.display = true;
      this.dataResult.repasActuel = this.calculeSommeActuelle();
      this.dataResult.repas2Vege = this.calculeSomme2Vege();
      this.dataResult.repasNorme = this.calculeSommeNorme();
      this.scroll();
    },
    prixJours(somme) {
      return somme / 730;
    },
    nombreUsers() {
      return (
        this.nbUsers - this.nbChildren + this.nbChildren * this.partChildren
      );
    },
    calculeSommeNorme() {
      return (
        this.nombreUsers() *
        (2 * this.prixJours(this.repasCarneAnnuel) +
          this.prixJours(this.repasVegetarienAnnuel) * (this.nbEat - 2))
      );
    },
    calculeSomme2Vege() {
      return (
        (this.prixJours(this.repasCarneAnnuel) * (this.nbEat - 2) +
          2 * this.prixJours(this.repasVegetarienAnnuel)) *
        this.nombreUsers()
      );
    },
    calculeSommeCarne() {
      return (
        this.nombreUsers() * this.nbEat * this.prixJours(this.repasCarneAnnuel)
      );
    },
    calculeSommeActuelle() {
      let repas;
      if (this.nbEat - this.nbRepasCarne > 0) {
        repas =
          this.nombreUsers() *
          (this.nbRepasCarne * this.prixJours(this.repasCarneAnnuel) +
            this.prixJours(this.repasVegetarienAnnuel) *
              (this.nbEat - this.nbRepasCarne));
      } else {
        repas = this.calculeSommeCarne();
      }

      return repas;
    },
    scroll() {
      console.log(document.getElementById("app").scrollHeight);
      window.scrollTo({
        behavior: "smooth",
        left: 0,
        top: document.getElementById("app").scrollHeight
      });
    }
  }
};
</script>

<style scoped>
.home {
  min-height: 100vh;
  background-image: url("../assets/tas-billet.png");
  background-repeat: no-repeat;
  background-position: 100% 100%;
}

.full {
  background-color: red;
  height: 100%;
  width: 100%;
}

img {
  position: absolute;
  right: 0;
  bottom: 0;
  max-width: 58%;
}

p {
  font-weight: 600;
  font-size: 35px;
  line-height: 54px;
  letter-spacing: 0.894844px;
  margin-bottom: 3rem;
}

form {
  z-index: 2;
}

select,
input[type="number"] {
  width: 70px;
  text-align: center;
  /* padding-left: 10px; */
  text-align-last: center;
  font-weight: bold;
  border-bottom: 4px solid #211987;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

/* Chrome */
input::-webkit-inner-spin-button,
input::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Opéra*/
input::-o-inner-spin-button,
input::-o-outer-spin-button {
  -o-appearance: none;
  margin: 0;
}

button {
  background-color: #211987;
  padding: 9px 30px;
  color: white;
  font-weight: bold;
  font-size: 35px;
  line-height: 54px;
  text-align: center;
  letter-spacing: 0.894844px;
  text-transform: capitalize;
}
</style>
