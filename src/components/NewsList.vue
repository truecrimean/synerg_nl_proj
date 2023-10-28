<script setup>
import { ref, watch } from 'vue';
import { onMounted } from 'vue'
import NewsListItem from "@/components/NewsListItem.vue";

let datalink = 'https://newsdata.io/api/1/news?apikey=pub_319138aec4cb780650c15152c47d861c4895c&q=новости';

const scrollCorrector = 0;
let data = ref({
  loading: false,
  items: [],
  pageCount: 0,
  nextPage: '',
  dataLink: datalink,
});

function getMorePosts() {
  window.onscroll = () => {
    setTimeout(()=>{
      let parEl = document.getElementById('news-list-wr');
      console.log('window.innerHeight: ', window.innerHeight);
      console.log('getBoundingClientRect: ', parEl.getBoundingClientRect().bottom + + scrollCorrector);
      let needToLoad = parEl.getBoundingClientRect().bottom - scrollCorrector < window.innerHeight;
      console.log('needToLoad: ', needToLoad);
      if (needToLoad) {
        loadPosts();
      }
    }, 500);
  }
}

function loadPosts() {
  let urlSuffix = data.value.nextPage === '' ? '' : 'page=' + data.value.nextPage;

  fetch(data.value.dataLink + urlSuffix)
      .then(
          r => r.json()
      )
      .then(d => {
        if (d.status === 'success') {

          data.value.items.push(...d.results);
          data.value.nextPage = d.nextPage;
          data.value.pageCount++;
        }
      });
}
watch(data.value.items, (newItems, oldItems) => {
  let myStorage = window.localStorage;
  if (myStorage){
    let articles = myStorage.getItem('articles');
    articles = (articles === null || articles === '') ? {} : JSON.parse(articles);
    for (let item of newItems) {
      if (!articles || articles[item.article_id] === undefined) {
        articles[item.article_id] = item;
      }
    }
    myStorage.setItem('articles', JSON.stringify(articles));
  }
});

onMounted(() => {
  loadPosts();
  //getMorePosts();
});

</script>

<template>
  <div id="news-list-wr">
    <div v-for="item in data.items" class="news-list-item-wr">
      <NewsListItem :postInfo="item"/>
    </div>
  </div>
</template>
