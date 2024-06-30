<template>
  <section class="section">
    <SharedBannerRelation data-sal="slide-left"
                          data-sal-delay="300"
                          data-sal-duration="150"
                          data-sal-easing="ease"
    class="banner"/>
    <p class="text" data-sal="fade"
        data-sal-duration="2000">Avenir Immobilier est la plateforme numéro 1 pour trouver et vendre des biens immobiliers en France. Finies les recherches interminables, trouvez le bien parfait en quelques clics.</p>
  </section>
</template>

<script>
export default {
  name: "RelationSection"
}
</script>

<style scoped>
.section {
  height: 643px;
  background: #dbae5f;
  margin-top: -80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.text {
    color: white;
    margin-top: 70px;
}
@media screen and (max-width: 860px) {
    .section {
        height: unset;
    }
    .text {
        margin-top: unset;
        margin-bottom: 140px;
    }
    .banner {
        margin-top: 160px;
    }
}
</style>
