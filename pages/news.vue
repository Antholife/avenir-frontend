<script>
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
      news: [],
      error: null,
    }
  },
  async mounted() {
    try {
      const response = await axios.get('http://localhost:1337/api/newss?populate=photo')
      this.news = response.data.data
    } catch (error) {
      this.error = error;
    }
  },
};
</script>
<template>
  <div class="container" style="margin-top: 60px">
    <div class="col" v-for="oneNews in news" style="padding: 30px 200px; display: flex; align-items: center; flex-direction: column; justify-content: center">
      <News :title="oneNews.attributes.title" :link="oneNews.attributes.link" :description="oneNews.attributes.description" :img="oneNews.attributes.photo.data.attributes.url"/>
    </div>
  </div>
</template>
