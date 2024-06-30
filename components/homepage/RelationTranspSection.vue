<template>
  <section class="section">
    <div class="wrapper">
      <div class="leftContainer" data-sal="slide-left"
           data-sal-delay="200"
           data-sal-duration="150"
           data-sal-easing="ease">
        <img style="border-radius: 20px" src="@/assets/homepage/relationTranspSection/relationTransp.png" :width=491 :height=634 alt="relation transparente">
      </div>
      <div class="rightContainer" data-sal="slide-right"
           data-sal-delay="400"
           data-sal-duration="150"
           data-sal-easing="ease">
        <img class="ellipse" src="@/assets/homepage/relationTranspSection/ellipse.svg" :width=167 :height=62 alt="line">
        <h2 class="overrideTypo">Une relation transparente.</h2>
        <p class="overrideTypoHtml">Chez Avenir Immobilier, nous mettons un point d'honneur à assurer une transparence totale entre acheteurs et vendeurs. Tous les prix sont clairement affichés et les conditions sont explicitement définies dès le départ. Ainsi, chaque partie sait exactement à quoi s'attendre, évitant toute confusion ou malentendu. Notre engagement envers la clarté et l'intégrité fait de nous le choix de confiance pour vos transactions immobilières.</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "BullshitSection"
}
</script>

<style scoped>
   .wrapper {
     margin: auto;
     max-width: 1165px;
     padding-left: 137px;
     display: flex;
     padding-right: 138px;
    }
   .overrideTypo {
       position: relative;
       font-family: 'Poppins', sans-serif;
       color: black;
       z-index: 1;
   }
   .overrideTypoHtml {
       margin-top: 42px;
       font-weight: 500;
       text-align: left;
   }
   .leftContainer {
       margin: -60px 178px 195px 0;
   }
   .section {
       background-color: #FFFFFF;
   }
   .rightContainer {
       margin-top: 100px;
       position: relative;
   }
   @media screen and (max-width: 1390px) {
       .wrapper {
           flex-direction: column;
           align-items: center;
       }
       .leftContainer {
           margin: -60px 0 0 0;
       }
       .rightContainer {
           margin-top: 50px;
           margin-bottom: 120px;
           text-align: center;
       }
       .overrideTypoHtml {
           text-align: center;
       }
   }
  .ellipse {
    position: absolute;
    top: 24px;
    left: 238px;
    z-index: 0;
  }
</style>
