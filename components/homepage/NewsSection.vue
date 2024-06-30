<script>
import axios from "axios";

export default {
    name: "NewsSection",
    data() {
        return {
            news: [],
            error: null,
        }
    },
    async mounted() {
        try {
            const response = await axios.get('http://localhost:1337/api/news?populate=img')
            this.news = response.data.data
        } catch (error) {
            this.error = error;
        }
    },
}
</script>

<template>
  <section class="section">
    <h1>Les news</h1>
    <div class="container">
      <div class="col" v-for="oneNews in news">
        <SharedNewsShared :date="oneNews.attributes.date" :text="oneNews.attributes.text" :img="oneNews.attributes.img.data.attributes.url"/>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}
.col {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
@media screen and (max-width: 1360px){
  .container {
    flex-direction: column;
    align-items: center;
  }
    .col {
        margin-bottom: 50px;
    }
}
.section {
  background: white;
  display: flex;
  position: relative;
  padding: 76px 104px 76px 84px;
  flex-direction: column;
}

h1 {
  color: black;
}
</style>
