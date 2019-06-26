<template>
  <nav class="flex justify-between">
    <div>
      <img src="https://fontmeme.com/images/Greenpeace-logo.png" alt>
    </div>
    <div>
      <ul class="flex text-3xl">
        <li class="font-bold">
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
</style>
