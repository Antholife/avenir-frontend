<template>
  <section class="section">
   <h2 data-sal="slide-left"
       data-sal-delay="200"
       data-sal-duration="300"
       data-sal-easing="ease"
       class="title">Les domaines qu'on couvre.</h2>
    <p data-sal="zoom-in"
       data-sal-delay="420"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim">ACHAT</p>
    <p data-sal="zoom-in"
       data-sal-delay="460"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim">VENTE</p>
    <p data-sal="zoom-in"
       data-sal-delay="500"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim1">LOCATION</p>
    <p data-sal="zoom-in"
       data-sal-delay="540"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim2">GESTION</p>
    <p data-sal="zoom-in"
       data-sal-delay="580"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim3">COPROPRIÉTÉ</p>
    <p data-sal="zoom-in"
       data-sal-delay="620"
       data-sal-duration="1000"
       data-sal-easing="ease"
       class="override anim3">CONSEIL</p>
  </section>
</template>

<script>
export default {
  name: "domainSection"
}
</script>

<style scoped>
  .section {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: white;
    padding: 156px 0 133px 0;
    text-align: center;
  }
  .title {
    font-family: 'Poppins', sans-serif;
    margin-bottom: 92px;
    color: black;
  }
  .override {
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 95px;
    line-height: 125px;
    font-weight: 400;
    color: #FFF;
    margin: 0;
      animation: colorChange 4s forwards;
  }
  .anim {
    animation-delay: 0.5s;
  }
  .anim1 {
    animation-delay: 1.5s;
  }
  .anim2 {
    animation-delay: 2.5s;
  }
  .anim3 {
    animation-delay: 3.5s;
  }
  @keyframes colorChange {
    0% {
      color: #FFF;
    }
    25% {
      color: #e4c07f;
    }
    50% {
      color: #dbae5f;
    }
    100% {
      color: #dbae5f;
    }
  }
</style>
