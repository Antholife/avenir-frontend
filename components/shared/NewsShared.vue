<script setup>
defineProps({
  date: {
    type: String,
  },
  text: {
    type: String,
  },
  img: {
    type: String,
  },
})
</script>

<template>
  <div data-sal="slide-up"
       data-sal-delay="200"
       data-sal-duration="400"
       data-sal-easing="ease"
       class="ctnNews">
    <p>{{date}}</p>
    <hr />
    <p class="text">{{text}}</p>
    <img :src="`http://localhost:1337${img}`" alt="icon" />
  </div>
</template>

<script>
import sal from "sal.js";
export default {
  name: "NewsShared",
  mounted() {
    sal();
  },
}
</script>

<style scoped>
  .ctnNews {
    background: transparent;
    display: flex;
    flex-direction: column;
    max-width: 376px;
    cursor: pointer;
  }
  .text {
    font-size: 16px;
    font-weight: 500;
    line-height: 24px;
  }
  p {
    font-size: 14px;
    font-weight: 600;
  }
  hr {
    border: 1px solid #000000;
    width: 100%;
    margin: 0;
  }
</style>
