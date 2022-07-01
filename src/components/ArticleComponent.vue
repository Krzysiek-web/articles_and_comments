<template>
  <div>
    <article v-for="article in articles" :key="article.id">
      <div class="article">
        <h1 class="article_title">{{ article.title }}</h1>
        <p class="content">{{ article.content }}</p>
        <h5 class="publication_date">
          Data dodania {{ article.publishingDate }}
        </h5>
      </div>
      <section>
        <h3 style="margin: 20px 0; text-decoration: underline">Komentarze</h3>
        <article v-for="comments in article.comment" :key="comments.id">
          <div class="comments">
            <h3 class="nickname">{{ comments.nickname }}</h3>
            <p class="content">{{ comments.content }}</p>
            <h5 class="publication_date">Data dodania {{date = new Date(comments.publishingDate)}}
            </h5>
          </div>
        </article>
      </section>
    </article>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: {
    id: {
      type: [Number, String],
      required: true,
    },
  },
  data() {
    return {
      articles: [],
    };
  },
  async created() {
    try {
      const getList = "http://127.0.0.1:8000/api/articles/?id=" + this.id;
      const response = await axios.get(getList);
      this.articles = response.data;
      this.error = "";
    } catch (err) {
      this.error = "Wystąpił błąd";
    }
  },
};
</script>

<style lang="scss" scoped="true">
.article {
  margin-top: 20px;
  border: 2px solid grey;
}
.article_title {
  padding: 10px;
}
.content {
  line-height: 1.3;
  text-align: justify;
  padding: 10px;
}
.comments {
  margin: 10px 0;
  border: 2px solid grey;
}
.publication_date {
  padding: 10px;
}
.nickname {
  padding: 10px;
}
</style>
