<template>
  <div class="footer flex justify-center my-10">
    <a href="#">À propos de nous</a>
    <a href="#">Conditions générales d'utilisation</a>
    <a href="#">Ressources</a>
    <a href="#">Confidentialité des données personnelles</a>
    <a href="#">Contact</a>
    <a href="#">Connexion</a>
    <a href="#">
      <i class="fab fa-facebook-f"></i>
    </a>
    <a href="#">
      <i class="fab fa-twitter"></i>
    </a>
  </div>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  margin-right: 3rem;
  font-weight: bold;
  font-size: 15px;
  line-height: 23px;
  letter-spacing: 0.894844px;
}

@media only screen and (max-width: 731px) {
  .footer {
    flex-direction: column;
    margin-left: 30px;
  }

  a {
    margin-bottom: 10px;
  }
}
</style>
