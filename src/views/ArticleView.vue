<script setup>
import ArticlePage from "@/components/ArticlePage.vue";

const props = defineProps({
  article_id: {
    type: String,
    required: true
  }
})
</script>

<template>
  <main id="base-news-wr">
    <ArticlePage :article_id="props.article_id"/>
  </main>
</template>
