<template>
  <div class="nav">
    <div class="in">
      <h3 data-sal="fade"
          data-sal-delay="100"
          data-sal-duration="150"
          data-sal-easing="ease">
        <NuxtLink class="link" :to="'/'">
          Avenir Immobilier
        </NuxtLink>
      </h3>
      <div class="panel">
        <NuxtLink class="link" :to="'/services'">Actualités</NuxtLink>
        <NuxtLink class="link" :to="'/sales'">Vente/Achat</NuxtLink>
        <NuxtLink class="link" :to="'/manage'">Location</NuxtLink>
        <NuxtLink class="link" :to="'/location'">Gestion locative</NuxtLink>
        <NuxtLink class="link" :to="'/syndic'">Syndicat de copropriété</NuxtLink>
        <NuxtLink class="link" :to="'/advice'">Conseil</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
import sal from 'sal.js'
sal();
export default {
  name: "Nav",
}
</script>

<style scoped>

.panel {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.link {
  margin: 0 10px;
  color: white;
  text-decoration: none;
  font-weight: 500;
  cursor: pointer;
  &:hover {
    color: #dbae5f;
  }
}

.in {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.nav {
  text-align: center;
  z-index: 999;
  width: 100%;
  position: fixed;
  background-color: black;
  top: 0;
  left: 0;
}
</style>
