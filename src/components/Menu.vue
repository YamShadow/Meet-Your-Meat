<template>
  <nav class="flex justify-between">
    <div>
      <img src="../assets/logo_hor.png" alt>
    </div>
    <div>
      <ul class="flex text-3xl">
        <li class="mobile font-bold">
          <a href="#">
            <p>Eco'nomise</p>
            <div class="line"></div>
          </a>
        </li>
        <li>
          <a href="https://www.cantineverte.fr/">J'agis</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Menu"
};
</script>

<style scoped>
li {
  padding-right: 3rem;
}

img {
  max-height: 50px;
}

.line {
  background: #211987;
  width: 100%;
  height: 11px;
}

@media only screen and (max-width: 731px) {
  .mobile {
    display: none;
  }

  img {
    max-width: 150px;
  }

  a {
    font-size: 18px;
  }
}
</style>
