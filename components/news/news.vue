<template>
  <a :href="link" style="text-decoration: none; width: 100%;" target="_blank">
    <section :style="{ backgroundColor: bgColor }" class="article-section">
      <img width="500px" height="300px" style="border-radius: 20px" :src="`http://localhost:1337${img}`" :alt="title" />
      <div style="text-align: left">
        <h2 style="text-align: left">{{ title }}</h2>
        <p style="color: #FFFFFF; font-weight: 400; text-align: left"> {{ description }}</p>
      </div>
    </section>
  </a>
</template>

<script setup>
defineProps({
  title: {
    type: String,
  },
  link: {
    type: String,
  },
  description: {
    type: String,
  },
  img: {
    type: String,
  },
})
</script>


<style scoped>
.article-section {
  gap: 60px;
  width: 100%;
  display: flex;
  align-items: center;
  border-radius: 20px;
  background-color: #dbae5f;
  color: #FFFFFF;
  padding: 40px;
}
</style>
