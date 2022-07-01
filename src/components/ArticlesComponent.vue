<template>
  <div>
    <span v-if="error">{{ error }}</span>
    <ul>
      <li v-for="article in articles" :key="article.id">
        <router-link style="color:black; text-decoration:none"
          :to="{
            name: 'article',
            params: {
              id: article.id,
            },
          }"
        >
          <h3>{{ article.title }}</h3>
          <p>{{ article.content }}</p>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'


export default {
  data() {
    return {
      articles: [],
      error: "",
    };
  },
  async created() {
    try {
      const getList = 'http://127.0.0.1:8000/api/articles/'
            const response = await axios.get(getList);
            this.articles = response.data;
            this.error = '' 
    } catch (err) {
      this.error = "Wystąpił błąd";
    }
  },
};
</script>

<style lang="scss" scoped>

ul {
  display: flex;
  flex-direction: column;
  align-items: center;
  list-style: none;

  li {
    h3 {
      margin: 10px;
    }
    width: 50%;
    max-height: 110px;
    overflow: hidden;
    margin: 5px;
    padding: 5px;
    border: 2px solid grey;
  }
  
}
</style>
