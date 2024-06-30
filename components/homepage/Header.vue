<template>
  <section class="section">
    <div class="leftContainer">
      <h1 data-sal="slide-up"
          data-sal-delay="250"
          data-sal-duration="150"
          data-sal-easing="ease">LA PLATEFORME n°1 POUR VOS<br /><span class="overrideTitle"> PROJETS IMMOBILIERS</span></h1>
      <div class="buttonsRow" data-sal="slide-down"
           data-sal-delay="400"
           data-sal-duration="150"
           data-sal-easing="ease">
        <NuxtLink  :to="'/connect'" class="buttonLeft">Je suis un locataire / propriétaire</NuxtLink>
        <NuxtLink :to="'/map'" class="buttonRight">Voir les locations disponibles</NuxtLink>
      </div>
    </div>
    <div data-sal="slide-up"
         data-sal-delay="300"
         data-sal-duration="150"
         data-sal-easing="ease">
      <img src="@/assets/homepage/headerSection/rightImg.png" :width=465 :height=588 alt="location">
    </div>
  </section>
</template>

<script>

import sal from 'sal.js'
export default {
  name: "Header",
  mounted() {
    sal();
  }
}
</script>

<style scoped>
.section {
  display: flex;
  justify-content: space-between;
  margin: 180px auto 10px;
  padding: 0 131px 0 138px;
  max-width: 1172px;
}
@media screen and (max-width: 1200px) {
    .section {
        flex-direction: column;
        align-items: center;
    }
    .leftContainer {
        max-width: unset;
        align-items: center;
        text-align: center;
        margin-bottom: 30px;
    }
}

.buttonsRow {
  display: flex;
  flex-direction: row;
}
.buttonRight {
  display: flex;
  justify-content: center;
  align-items: center;
  background: #dbae5f;
  width: 260px;
  height: 46px;
  border-radius: 8px;
  color: #FFFFFF;
  border: none;
  cursor: pointer;
  font-family: 'IntegralCF-Regular', sans-serif;
  font-size: 12px;
  font-weight: 400;
  text-decoration: none;
}
.buttonLeft {
  background: #FFFFFF;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 12px;
  font-weight: 400;
  color: black;
  width: 260px;
  height: 46px;
  border-radius: 8px;
  margin-right: 22px;
  cursor: pointer;
  border: none;
  text-decoration: none;
  font-family: 'IntegralCF-Regular', sans-serif;
}
.leftContainer {
  display: flex;
  flex-direction: column;
  max-width: 700px;
  color: white;
}
.overrideTitle {
  color: #000000;
  -webkit-text-stroke: 1px #dbae5f;
    animation: colorChange 3s infinite;
}

@keyframes colorChange {
    0% {
        color: #000000;
    }
    50% {
        color: #dbae5f;
    }
    100% {
        color: #000000;
    }
}
</style>
