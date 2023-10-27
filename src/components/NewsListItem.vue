<script setup>
import imgTemplate from "../assets/news-template.jpeg"
const props = defineProps(['postInfo']);
let image = props.postInfo.image_url ? props.postInfo.image_url : imgTemplate;
</script>
<template>
  <div class="item">
    <div class="media_section">
      <img :src="image"/>
    </div>
    <div class="content_section">
      <h2>{{postInfo.title}}</h2>
      <p>{{postInfo.description}}</p>
    </div>

  </div>
</template>

<style scoped>
  .news-list-item-wr .item {
    display: flex;
    margin-bottom: 20px;
  }
  .news-list-item-wr .media_section {
    padding: 0 20px;
  }
  .news-list-item-wr .media_section img {
    max-width: 250px;
    height: auto;
  }
</style>
