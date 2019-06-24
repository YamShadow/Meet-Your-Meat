<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
        <HelloWorld msg="Welcome on Meet your Meat"/>

        <form action="post" @submit="send">
            <label for="nbUsers">Nombre de personnes dans votre foyer</label>
            <input type="number" min="0" v-model="nbUsers" name="nbUsers" id="nbUsers">
            <label for="nbChildren">Nombre d'enfants parmis vous ?</label>
            <input
                type="number"
                :max="nbUsers"
                min="0"
                v-model="nbChildren"
                name="nbChildren"
                id="nbChildren"
            >
            <label for="nbRepasCarne">Nombre de repas avec de la viande ?</label>
            <input
                type="number"
                min="0"
                max="14"
                v-model="nbRepasCarne"
                name="nbRepasCarne"
                id="nbRepasCarne"
            >
            <button>Clique sur moi</button>
        </form>

        <div v-if="dataResult.display">
            <p>Somme repas carnivore</p>
            <p>{{ dataResult.repasActuel.toFixed(2) }}</p>
            <p>Somme repas 2 legume</p>
            <p>{{ dataResult.repas2Vege.toFixed(2) }}</p>
            <p>Somme repas norme</p>
            <p>{{ dataResult.repasNorme.toFixed(2) }}</p>
            <div>
                <h2>Actuel / Norme</h2>
                <div>
                    <p>Economie 1 semaine</p>
                    <p>{{ (dataResult.repasActuel - dataResult.repasNorme).toFixed(2) }}</p>
                </div>
                <div>
                    <p>Economie 1 mois</p>
                    <p>{{ ((dataResult.repasActuel - dataResult.repasNorme) * 4.33).toFixed(2) }}</p>
                </div>
                <div>
                    <p>Economie 1 ans</p>
                    <p>{{ ((dataResult.repasActuel - dataResult.repasNorme) * 52).toFixed(2) }}</p>
                </div>
            </div>

            <div>
                <h2>Actuel / 2 végé</h2>
                <div>
                    <p>Economie 1 semaine</p>
                    <p>{{ (dataResult.repasActuel - dataResult.repas2Vege).toFixed(2) }}</p>
                </div>
                <div>
                    <p>Economie 1 mois</p>
                    <p>{{ ((dataResult.repasActuel - dataResult.repas2Vege) * 4.33 ).toFixed(2)}}</p>
                </div>
                <div>
                    <p>Economie 1 ans</p>
                    <p>{{ ((dataResult.repasActuel - dataResult.repas2Vege) * 52).toFixed(2) }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
    name: "home",
    components: {
        HelloWorld
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
    methods: {
        send(e) {
            e.preventDefault();
            this.dataResult.display = true;
            this.dataResult.repasActuel = this.calculeSommeActuelle();
            this.dataResult.repas2Vege = this.calculeSomme2Vege();
            this.dataResult.repasNorme = this.calculeSommeNorme();
        },
        prixJours(somme) {
            return somme / 730;
        },
        nombreUsers() {
            return (
                this.nbUsers -
                this.nbChildren +
                this.nbChildren * this.partChildren
            );
        },
        calculeSommeNorme() {
            return (
                this.nombreUsers() *
                (2 * this.prixJours(this.repasCarneAnnuel) +
                    this.prixJours(this.repasVegetarienAnnuel) *
                        (this.nbEat - 2))
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
                this.nombreUsers() *
                this.nbEat *
                this.prixJours(this.repasCarneAnnuel)
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
        }
    }
};
</script>
