<template>
  <section class="section">
    <img data-sal="slide-right"
         data-sal-delay="300"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img0" src="@/assets/homepage/collabSection/cornerLeft.png" :width=241 :height=187 alt="persona">
    <img data-sal="slide-bottom"
         data-sal-delay="550"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img1" src="@/assets/homepage/collabSection/middleTop.png" :width=175 :height=212 alt="persona1">
    <img data-sal="slide-left"
         data-sal-delay="420"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img2" src="@/assets/homepage/collabSection/rightCorner.png" :width=175 :height=212 alt="persona2">
    <img data-sal="slide-right"
         data-sal-delay="500"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img3" src="@/assets/homepage/collabSection/leftBottom.png" :width=241 :height=292 alt="persona3">
    <img data-sal="slide-up"
         data-sal-delay="350"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img4" src="@/assets/homepage/collabSection/middleBottom.png" :width=255 :height=118 alt="persona4">
    <img data-sal="slide-left"
         data-sal-delay="600"
         data-sal-duration="1000"
         data-sal-easing="ease"
         class="img5" src="@/assets/homepage/collabSection/rightBottom.png" :width=374 :height=177 alt="persona5">
    <h1 style="max-width: 710px; text-align: center"
        data-sal="zoom-out"
        data-sal-delay="450"
        data-sal-duration="300"
        data-sal-easing="ease"
    ><span class="title">déjà plus de</span><span class="override"> 250 collaborations</span></h1>
  </section>
</template>

<script>
export default {
  name: "CollabSection"
}
</script>

<style scoped>
.img0 {
  position: absolute;
  top: 0;
  left: 0;
}
.img1 {
  position: absolute;
  top: 71px;
  left: 41%;
}
.img2 {
  position: absolute;
  right: 116px;
  top: 0;
}
.img3 {
  position: absolute;
  bottom: 0;
  left: 160px;
}
.img4 {
  position: absolute;
  bottom: 0;
  left: 46%;
}
.img5 {
  position: absolute;
  bottom: 0;
  right: 57px;
}
.section {
  height: 620px;
  background: black;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
.title {
  position: relative;
  width: 451px;
  text-align: center;
  z-index: 1;
}
.override {
  color: #dbae5f;
  width: 710px;
  display: block;
  position: relative;
}

</style>
