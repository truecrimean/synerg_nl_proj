<script setup>
 import NewsListItem from "@/components/NewsListItem.vue";
 import {ref, onMounted} from "vue";

 let data = ref({
   favorites: {},
 });
 function getFavorites() {
   let myStorage = window.localStorage;
   if (myStorage) {
     let favoritesIndxs = myStorage.getItem('favorites');
     let articles = myStorage.getItem('articles');
     articles = (articles === null || articles === '') ? [] : JSON.parse(articles);
     favoritesIndxs = (favoritesIndxs === null || favoritesIndxs === '') ? [] : JSON.parse(favoritesIndxs);
     favoritesIndxs.forEach((felement, findex) => {
       data.value.favorites[felement] = articles[felement];
     });
   }
 }

 onMounted(() => {
   getFavorites();
 })
</script>

<template>
  <div id="news-list-wr">
    <div v-for="item in data.favorites" class="news-list-item-wr">
      <NewsListItem :postInfo="item"/>
    </div>
  </div>
</template>

<style scoped>

</style>
