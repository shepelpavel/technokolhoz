<template>
  <div>
    <ul v-if="articles.length">
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="article.slug">
          {{ article.title ?? article.slug }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $content }) {
    const articles = await $content('articles')
      .only(['title', 'description', 'createdAt', 'slug'])
      .fetch()
    return { articles }
  },
}
</script>
