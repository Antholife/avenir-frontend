<template>
  <section class="section">
    <img data-sal="flip-left"
         data-sal-delay="100"
         data-sal-duration="400"
         data-sal-easing="ease"
         src="@/assets/homepage/reviewSection/client.png" :width=458 :height=493 alt="client">
    <div data-sal="flip-right"
         data-sal-delay="300"
         data-sal-duration="400"
         data-sal-easing="ease"
         class="rightContainer">
      <h3 data-sal="fade"
          data-sal-delay="600"
          data-sal-duration="400"
          data-sal-easing="ease"
          class="title">Jérôme, propriétaire satisfait</h3>
      <p data-sal="fade"
         data-sal-delay="700"
         data-sal-duration="400"
         data-sal-easing="ease"
      class="desc">
        Je suis très satisfait de la plateforme, j'ai pu trouver des acheteurs intéressés et sérieux pour mon bien immobilier.
        Très impliqué dans la vente de ma propriété, je suis ravi de pouvoir utiliser les services professionnels d'Avenir Immobilier.
        Merci à Avenir Immobilier !
         </p>
      <button data-sal="fade"
              data-sal-delay="600"
              data-sal-duration="400"
              data-sal-easing="ease"
              class="button">VOIR LES AUTRES AVIS</button>
    </div>
  </section>
</template>

<script>
export default {
  name: "ReviewSection"
}
</script>

<style scoped>
  .desc {
    font-family: 'Poppins', sans-serif;
    font-size: 16px;
    line-height: 22px;
    font-weight: 400;
    color: #000;
    margin-top: 20px;
      text-align: left;
    margin-bottom: 60px;
      max-width: 500px;
  }
  .section {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 706px;
    background-color: #000;
    padding: 107px 0;
  }
  .rightContainer {
    display: flex;
    flex-direction: column;
    background-color: #FFF;
    width: 526px;
    height: 355px;
    padding-left: 50px;
    margin-left: -90px;
      border-radius: 8px;
  }
  .title {
    font-family: 'Poppins', sans-serif;
    font-size: 25px;
    line-height: 38px;
    font-weight: 800;
    color: black;
  }
  .button {
    width: 204px;
    height: 46px;
    border-radius: 8px;
    background-color: #dbae5f;
    color: #FFF;
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 12px;
    line-height: 16px;
    font-weight: 400;
    border: none;
    cursor: pointer;
  }
  @media screen and (max-width: 960px){
      .rightContainer {
          margin-left: 0;
      }
      .desc {
          margin-bottom: 30px;
      }
      .section {
          flex-direction: column;
      }
      .button {
          margin-bottom: 30px;
      }
  }
</style>
