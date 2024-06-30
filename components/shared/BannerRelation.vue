<template>
  <div class="container">
    <img
        data-sal="fade"
        data-sal-delay="500"
        data-sal-duration="400"
        data-sal-easing="ease"
        src="@/assets/shared/bannerRelation/logoFnaim.svg" :width=200 :height=160 alt="logoFnaim">
    <img
        data-sal="fade"
        data-sal-delay="600"
        data-sal-duration="400"
        data-sal-easing="ease"
            src="@/assets/shared/bannerRelation/logoBreeam.svg" :width=120 :height=120 alt="logoBreeam">
    <img data-sal="fade"
         data-sal-delay="700"
         data-sal-duration="400"
         data-sal-easing="ease"
         src="@/assets/shared/bannerRelation/logoAfnor.svg" :width=110 :height=70 alt="logoAfnor">
    <img data-sal="fade"
         data-sal-delay="800"
         data-sal-duration="400"
         data-sal-easing="ease"
         src="@/assets/shared/bannerRelation/logoCfei.svg" :width=180 :height=154 alt="logoCfei">
    <img
            data-sal="fade"
            data-sal-delay="900"
            data-sal-duration="400"
            data-sal-easing="ease"
            src="@/assets/shared/bannerRelation/logoNf.svg" :width=192 :height=130 alt="logoNf">
    <img data-sal="fade"
         data-sal-delay="1000"
         data-sal-duration="400"
         data-sal-easing="ease"
         src="@/assets/shared/bannerRelation/logoWell.svg" :width=168 :height=112 alt="logoWell">
  </div>
</template>

<script>
export default {
  name: "Banner"
}
</script>

<style scoped>
.container {
    position: relative;
  display: flex;
  align-items: center;
}
.container img {
  margin-right: 54px;
}
@media screen and (max-width: 860px) {
    .container {
        flex-direction: column;
    }
    .container img {
        margin-right: unset;
        margin-bottom: 54px;
    }
}
</style>
