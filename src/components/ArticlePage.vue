<script setup>
import imgTemplate from "../assets/news-template.jpeg";
const props = defineProps({
  article_id: {
    type: String,
    required: true
  }
})
function getArticle(id) {
  let article = null;
  let myStorage = window.localStorage;
  if (myStorage){
    let articles = myStorage.getItem('articles');
    articles = JSON.parse(articles);
    console.log(articles[id]);
    if (articles[id] !== undefined) {
      article = articles[id];
    }
  }

  return article;
}

const article = getArticle(props.article_id);
const img = article.image_url ? article.image_url : imgTemplate;
</script>

<template>
  <div id="article-wr">
    <h1>{{article.title}}</h1>
    <div class="media-section">
      <img :src="img">
      <div class="media-meta">
        <button class="favorite-btn"></button>
      </div>
    </div>
    <div class="content-section">
      {{article.content}}
    </div>
  </div>
</template>

<style scoped>
  .media-meta {
    display: flex;
    justify-content: flex-end;
    margin: 15px 0;
  }
  .favorite-btn {
    border: none;
    width: 20px;
    height: 20px;
    background: url("../assets/heart-regular.svg") center center transparent no-repeat;
  }
  .favorite-btn.checked {
    background: url("../assets/heart-solid.svg") center center transparent no-repeat;
  }
  .favorite-btn:hover {
    cursor: pointer;
  }
</style>