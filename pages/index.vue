<template>
  <div>
    <div v-for="(article, index) in articles" :key="index">
      <nuxt-link :to="article.path">{{ article.title }}</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  async asyncData({ $content }) {
    const articles = await $content('articles')
      .limit(5)
      .fetch()

    return {
      articles
    }
  }
}
</script>
