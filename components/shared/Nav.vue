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
      <div class="burger" @click="toggleMenu">
        &#9776;
      </div>
      <div :class="['panel', { 'panel-active': isMenuActive }]">
        <NuxtLink class="link" :to="'/news'">Actualités</NuxtLink>
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
  data() {
    return {
      isMenuActive: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuActive = !this.isMenuActive;
    }
  }
}
</script>


<style scoped>
.nav {
  text-align: center;
  z-index: 999;
  width: 100%;
  position: fixed;
  background-color: black;
  top: 0;
  left: 0;
}

.in {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.panel {
  display: flex;
  justify-content: end;
  align-items: center;
  transition: max-height 0.3s ease-out;
  max-height: 0;
  overflow: hidden;
  flex-direction: column;
  width: 100%;
}

.panel-active {
  max-height: 300px; /* Adjust according to the number of items */
}

.link {
  margin: 10px 0;
  color: white;
  text-decoration: none;
  font-weight: 500;
  cursor: pointer;
  &:hover {
    color: #dbae5f;
  }
}

.burger {
  display: none;
  font-size: 30px;
  cursor: pointer;
}

@media (min-width: 768px) {
  .panel {
    flex-direction: row;
    max-height: none;
  }

  .burger {
    display: none;
  }

  .link {
    margin: 0 10px;
  }
}

@media (max-width: 767px) {
  .burger {
    display: block;
  }

  .panel {
    flex-direction: column;
  }
}
</style>

