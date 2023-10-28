<script setup>
import imgTemplate from "../assets/news-template.jpeg";
const props = defineProps(['postInfo']);
let image = props.postInfo.image_url ? props.postInfo.image_url : imgTemplate;
</script>
<template>
  <div class="item">
    <div class="media_section">
      <a :href="'/article/' + postInfo.article_id"><img :src="image"/></a>
    </div>
    <div class="content_section">
      <h2><a :href="'/article/' + postInfo.article_id">{{postInfo.title}}</a></h2>
      <p><a :href="'/article/' + postInfo.article_id">{{postInfo.description}}</a></p>
    </div>
  </div>
</template>

<style scoped>
  .news-list-item-wr .item {
    display: flex;
    margin-bottom: 20px;
  }
  .news-list-item-wr .item a {
    color: var(--vt-c-black-mute);
  }
  .news-list-item-wr .item a:hover {
    color: var(--vt-c-black);
    background-color: transparent;
  }
  .news-list-item-wr .media_section {
    padding: 0 20px;
  }
  .news-list-item-wr .media_section img {
    max-width: 250px;
    height: auto;
  }
  @media (min-width: 1280px) {
    .news-list-item-wr .media_section {
      flex: 0 0 295px;
    }
  }
</style>
