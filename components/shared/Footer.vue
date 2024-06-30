<template>
  <section class="footer">
    <h3 data-sal="slide-right"
        data-sal-delay="200"
        data-sal-duration="400"
        data-sal-easing="ease"
    >Avenir Immobilier</h3>
    <p data-sal="slide-up"
       data-sal-delay="200"
       data-sal-duration="400"
       data-sal-easing="ease"
    >Site développé par Anthony CHAHAT</p>
    <h3 data-sal="slide-left"
        data-sal-delay="200"
        data-sal-duration="400"
        data-sal-easing="ease" style="cursor: pointer">contact</h3>
  </section>
</template>

<script>
export default {
  name: "Footer"
}
</script>

<style scoped>
 p {
   font-size: 24px;
   font-weight: 500;
 }
 .footer {
   background: #F2F2F2;
   display: flex;
   align-items: center;
   justify-content: space-between;
   color: black;
   padding: 0 50px;
 }
</style>
